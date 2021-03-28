## Introduction to NVBench

This repository contains the corpus of NL2VIS, with JSON format and Vega-Lite format.

- **NVBench.json** stores the JSON format of (NL, VIS) pairs in the NVBench benchmark.

- **NVBench_Vega** contains all (NL, VIS) pairs in the NVBench benchmark, and renders the VIS using the [Vega-Lite](https://vega.github.io/vega-lite/) visualization library.

- **database** contains all DB used by the NVBench benchmark.

### NVBench.json

#### (NL, VIS) JSON format
Each (NL, VIS) pair is denoted as a JSON object in NVBench.json, with the following fields:
- `key`: the id of the (NL, VIS) pair in NVBench benchmark
- `vis_query`: contains the query for VIS, with two parts: `vis_part` and `data_part`.
- `chart`: the visualization types: `Bar`, `Pie`, `Line`, `Scatter`, `Stacked Bar`, `Grouping Line`, and `Grouping Scatter`.
- `db_id`: the visualization comes from which database.
- `vis_obj`: the JSON format for representing a visualization object, with `chart` (chart type), `x_name` (name of the X-axis), `y_name`(name of the Y-axis), `x_data` (data for the X-axis), `y_data` (data for the Y-axis), `classify` (Z-axis data, for stacked bar, grouping line, and grouping scatter chart.)
- `nl_queries`: contains the NL queries for querying this visualization object.

Below is an example:
```
"8": {
        "vis_query": {
            "vis_part": "Visualize PIE",
            "data_part": {
                "sql_part": "SELECT Rank , COUNT(Rank) FROM Faculty GROUP BY Rank",
                "binning": ""
            },
            "VQL": "Visualize PIE SELECT Rank , COUNT(Rank) FROM Faculty GROUP BY Rank"
        },
        "chart": "Pie",
        "hardness": "Easy",
        "db_id": "activity_1",
        "vis_obj": {
            "chart": "pie",
            "x_name": "Rank",
            "y_name": "CNT(Rank)",
            "x_data": [
                [
                    "AssocProf",
                    "AsstProf",
                    "Instructor",
                    "Professor"
                ]
            ],
            "y_data": [
                [
                    8,
                    15,
                    8,
                    27
                ]
            ],
            "classify": [],
            "describe": "GROUP BY Rank"
        },
        "nl_queries": [
            "A pie chart showing the number of faculty members for each rank.",
            "What is the number of the faculty members for each rank? Return a pie.",
            "Compute the total the number of rank across rank as a pie chart."
        ]
    }
```