# forplotR example: MONITORA Maltese-cross plot

Supplementary example for the manuscript describing the R package **forplotR**.

Station EA-1 of a MONITORA forest plot (ICMBio): four arms of 10 subplots of 10 x 10 m in a Maltese cross (`input_type = "monitora"`).

## Files

- `index.html`: field report written by `forplot_balance()` (collection balance, subplot pages, floristics and phytosociology, checklist; it can be printed to PDF from the browser). The button at the top opens the map.
- `map.html`: interactive plot map written by `forplot_map()` (Leaflet), with a button back to the report. The popups of collected trees link to the digitised herbarium specimen in JABOT (RB herbarium).

## Data

Real census data from Parque Nacional Montanhas do Tumucumaque (Amapa, Brazil), distributed with the package as the dataset `TUM`.

## How it was made

```r
fp <- file.path(tempdir(), "TUM.xlsx")
openxlsx::write.xlsx(forplotR::TUM, fp)
forplot_map(fp, input_type = "monitora", station_name = "EA-1",
            vertex_coords = c(2.0916581, -53.1489687), language = "en",
            herbaria_lookup = TRUE, herbaria = "RB",
            report_url = "index.html")
forplot_balance(fp, input_type = "monitora", station_name = "EA-1", language = "en",
                map_url = "map.html")
```

Team names were replaced by a generic label for double-anonymous review. Of the 64 specimens matched in JABOT, the 48 with a digitised image are linked, in the form that opens the image directly (`codtestemunho=<number>&arquivo=<barcode>.dzi`); the 16 not yet digitised are not linked.
