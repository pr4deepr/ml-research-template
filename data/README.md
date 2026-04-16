# Data Provenance

## Source
- **Origin:** [Where the data came from -- instrument, database, public dataset, collaborator]
- **Acquisition date:** [When]
- **Format:** [e.g., HDF5, TIFF, CSV, DICOM, Parquet]

## Preprocessing
- **Steps:** [List every transformation from raw to training-ready, in order]
- **Scripts:** [Which scripts perform preprocessing, in order]

## Splits
- **Train / Val / Test:** [How many samples in each, what split strategy]
- **Split by:** [e.g., subject, patient, random -- and why this unit was chosen]
- **Stratification:** [What was balanced across splits -- class labels, demographics, etc.]

## Versions

| Version | Date | Changes | Experiments using it |
|---------|------|---------|---------------------|
| v1 | [Date] | Initial | [List] |

## Effective sample size
- **Reported N:** [Total observations]
- **Independent N:** [Truly independent samples]
- **Why they differ:** [e.g., multiple timepoints per subject, multiple crops per image]
