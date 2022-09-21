# Required Fields

The first tab of the Excel spreadsheet, **zoningedits**, is required regardless of the ADU policy. To begin, a user must populate Column A, Zone Code, with rows corresponding to each of the base zoning districts in the municipality. While the tool will likely function with any text string, we highly recommend using a concatenation of the Municipal ID and the abbreviation for the zoning district. Regardless, the Zone Code field must be identical in structure to the Zone Code field in the [Zoning Spatial Input](../spatial-inputs/3-1.-zoning.md), as these two fields will be used to join the tabular and spatial data in the automated analysis.

Once Column A is complete, a user must populate columns B, C, D, and E with 1s and 0s describing whether that ADU Typology is allowable in that zoning district. Columns F through AG may be ignored; they are read-only fields that reference values specified in the other four tabs.

![Required Inputs. Click to expand.](../../.gitbook/assets/Excel-Screenshot.png)

