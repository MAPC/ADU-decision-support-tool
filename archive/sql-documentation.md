# SQL Documentation

\##Install Postgres and PostGIS Postgres via pgAdmin - (https://www.pgadmin.org/download/)\[https://www.pgadmin.org/download/] PostGIS - (https://postgis.net/install/)\[https://postgis.net/install/] csvkit = (https://csvkit.readthedocs.io/en/latest/)\[https://csvkit.readthedocs.io/en/latest/]

\##Input Tables and Shapefiles In the testing directory there are two directories: shapefiles and tables. All of these tables and shapefiles are required to run tests and analyses in Postgres and PostGIS. Names need to match exactly or the scripts need to be updated. The following command are run in a terminal command line.

You will need a local postgres database instance running with a database set up for `beverly_adu`. The following strings are also use to connect to our production database pg.mapc.org. You will need the password and will insert that below in place of `{password}`

The following csv files should be in testing/tables. Run the following commands from the command line within that directory. `csvsql --db postgresql:///beverly_adu --insert zoningedits_s1.csv` `csvsql --db postgresql:///beverly_adu --insert structures_ov150sf_join_zp_dist.csv` `csvsql --db postgresql:///beverly_adu --insert table_structures_ov150sf_byparcel.csv`

These command will copy the tables from your local database to the production database `pg.mapc.org`. `pg_dump -C -h localhost -U postgres -t zoningedits_s1 beverly_adu | psql -h pg.mapc.org -U postgres beverly_adu` `pg_dump -C -h localhost -U postgres -t table_structures_ov150sf_byparcel beverly_adu | psql -h pg.mapc.org -U postgres beverly_adu`

The following table was replaced by `table_structures_ov150sf_byparcel` but I am keeping it in there for now. `pg_dump -C -h localhost -U postgres -t structures_ov150sf_join_zp_dist beverly_adu | psql -h pg.mapc.org -U postgres beverly_adu`

The following shapefiles should be in testing/shapefiles/input. Run the following commands from the command line within that directory. Check to make sure your shapefiles all have a projection after they are loaded if you have issues commands can be found below. They are examples that can be edited and run in pgAdmin on the database. `shp2pgsql aduboundary public.aduboundary | psql -h pg.mapc.org -d beverly_adu -U postgres shp2pgsql aduexclusions public.aduexclusions | psql -h pg.mapc.org -d beverly_adu -U postgres` `shp2pgsql allparcels public.allparcels | psql -h pg.mapc.org -d beverly_adu -U postgres` `shp2pgsql possible_parcels_s1 public.possible_parcels_s1 | psql -h pg.mapc.org -d beverly_adu -U postgres` `shp2pgsql zoning public.zoning | psql -h pg.mapc.org -d beverly_adu -U postgres`

\##Test Scripts to Set up Views Postgres test scripts are located in testing/scripts. Open pgAdmin and run the following scripts on your database to create the views. `effaduboundary.sql` `test_1.sql` `test_3.sql`

\##Shapfile Output from Test After your data has been imported and your views created navigate to the testing/shapefiles/output directory in your terminal. The following lines can be run to extract the results from the database as shapefiles. `pgsql2shp -f adu_fit_1 -h pg.mapc.org -u postgres -P {password} beverly_adu "select * from adu_fit_1"` `pgsql2shp -f adu_fit_3 -h pg.mapc.org -u postgres -P {password} beverly_adu "select * from adu_fit_3"` `pgsql2shp -f parcels_in_effaduboundary -h pg.mapc.org -u postgres -P {password} beverly_adu "select * from parcels_in_effaduboundary"`

\##Helpful scripts for setting up SRIDs on spatial data in the database.

Use the following 5 queries in pgAdmin to the check the srid of the shapefile. If any of them are 0 check out the projection on the original shapefile and then use the update the srid script query on the table. If you need to transform (reproject) then use the transform statement below to reproject using postgis.

Check srid script `SELECT ST_SRID(geom) from aduboundary` `SELECT ST_SRID(geom) from aduexclusions` `SELECT ST_SRID(geom) from allparcels` `SELECT ST_SRID(geom) from possible_parcels_s1` `SELECT ST_SRID(geom) from zoning`

Update srid script `UPDATE aduboundary SET geom = ST_SetSRID(geom,26986)`

`UPDATE aduexclusions SET geom = ST_SetSRID(geom,26986)`

`UPDATE allparcels SET geom = ST_SetSRID(geom,26986)`

`UPDATE possible_parcels_s1 SET geom = ST_SetSRID(geom,26986)`

Transform srid script `UPDATE zoning SET geom = ST_Transform(ST_SetSRID(geom,2249), 26986)`
