# Purpose of the Script

This tool is a comparison utility script designed to detect two primary issues: Parser issue and OCR issue. The output generated by the tool consists of a summary JSON file that provides basic stats and the count of OCR and Parser issues for entities present in each document. Additionally, analysis CSV files are also produced.

## Issues Defined

- **Parser issue:**
  Identified when the bounding box fails to encompass the entire text region, resulting in incomplete text capture. When users access the HITL worker UI, they adjust the bounding box to cover the entire text region and save their changes. This script highlights such discrepancies.

- **OCR issue:**
  Recognized when the bounding box does cover the entire text region, but the resultant text is not captured fully. These cases are flagged by the script.

## Inputs

- **project_id:** Provide the specific project ID.
  
- **Pre_HITL_Output_URI:** Input the GCS path containing pre-HITL processed JSONs.
  
- **Post_HITL_Output_URI:** Input the GCS path of post-HITL processed JSONs (those processed through HITL).

> **NOTE:** By default, the name of the Post-HITL JSON will differ from the original file name. It's essential to update this manually before utilizing the tool.

## Output Details

A result summary table is produced that distinctly highlights the count of both parser and OCR issues for each file. This table provides insights into pre and post-HITL entity modifications, and whether any bounding box coordinate mismatches emerged after post-HITL processing. Supporting images would demonstrate either the parser or OCR issue (as mentioned).

A summary JSON file is also generated, emphasizing counts of bounding box mismatches, OCR and Parser errors, and an analysis path to the result table for each of the processed files.

For a granular analysis of each file, refer to the CSV files located in the `analysis/` folder.

## Table Structure

The result output table is structured with the following columns:

- **File Name:** Displays the name of the file.
  
- **Entity Type:** Designates the entity type.
  
- **Pre_HITL_Output:** Shows the entity text before HITL intervention.
  
- **Pre_HITL_bbox:** Lists the bounding box coordinates pre-HITL.
  
- **Post_HITL_Output:** Represents the entity text post-HITL.
  
- **Hitl_update:** Indicates if a HITL update was applied to the particular entity.
  
- **Post_HITL_bbox:** Details the bounding box coordinates post-HITL.
  
- **Fuzzy Ratio:** Demonstrates the percentage match of the text.
  
- **Bbox_mismatch:** Flags instances where bounding box coordinates didn't match.
  
- **OCR issue:** Denotes if the issue was classified as an OCR Issue.
  
- **Parser issue:** Specifies if the issue was recognized as a Parser Issue.
