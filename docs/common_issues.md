# Common issues

Some errors may be reported when using antiSMASH.
The vast majority of these are input-related.
Common errors are listed here, along with possible solutions.

--------------------------

## "All records skipped"

This error will occur when there are no records within the input that are regarded as
significant enough to process.

By default, antiSMASH only processes the first 1,000 records in an input
(or as set with the `--limit` command line option).
If all of those first records are skipped, then the remainder will not be checked
and this error will be reported.


The main causes for a record being skipped are when it has:

- a length less than 1,000 nucleotides (or as set with the `--minlength` command line option)
- no genes present or found with genefinding (when submitting a GBK file to the webservice, no genefinding will take place)

Note: for antiSMASH inputs, the required features are `CDS`, not `gene`, as the `gene` features do not contain enough information.

**Possible fixes**:

- ensure at least one record is longer than the minimum length
- run your genefinding tool of choice and ensure that genes are annotated as you would like
- set the `--minlength` option to suit your inputs


## "All input records smaller than minimum length"

Similar to the "All records skipped" error above,
but mentioned only when *all* records are skipped due to being too short.


## "Feature type has invalid length: '...'"

This error occurs when a GFF file is provided for gene annotations
*and* a feature type is too long to be used as as a feature type in output GBK files.

The feature type of the first invalid type found is given in the error message.

**Possible fixes**:

Find all features with the type mentioned in the error, then remove or rename them.


## "Incomplete whole genome shotgun records are not supported"

This error will occur when one or more Genbank formatted inputs contains only whole genome shotgun references.
For example, the `JBLVKJ0100000001` RefSeq entry is currently annotated with this block and no sequence:

```
WGS         JBLVKJ010000001-JBLVKJ010000171
```


## "Invalid sideload annotations: 'tool' is a required property"

This error occurs when additional annotation information is given via the webservice or the `--sideload` command line option.

The typical cause for this is providing a file that is not in the required format.

**Possible fixes**:

Ensure that the file used is exported from a tool that *specifically* intends it to be used in antiSMASH.

Do not provide antiSMASH JSON output file as the input for sideloading.


## "Multiple CDS features have the same name for mapping: ..."

This error occurs when two or more CDS feature have the same identifier(s).
If a duplication is present, antiSMASH may provide misleading results.

The identifier of the first duplicate found is given in the error message.

**Possible fixes**:

Find the features with that identifier and either:

- remove all but one if they are exact duplicates
- change the identifiers to be unique (or add unique `locus_tag` qualifiers, if not already present)


## "No valid records found"

There main causes of this error are:

- the input file is empty
- there are errors in all records *and* the `--skip-sanitisation` command line option is present

**Possible fixes**:

Ensure the input is not empty.

If the `--skip-sanitisation` option was provided, disable it and find the errors within the inputs.


## "Record contains no sequence information"

This occurs when an input contains valid record identifiers (and, for GBK files, other required annotations),
but there is no sequence annotated in the input.

**Possible fixes**:

Remove any record in the input for which there is no sequence or include the sequence in the input.

--------------------------


## General formatting errors

There is a wide variety of formatting errors that can be present in inputs.
Not all annotation tools follow the standards for the Genbank file format.
When errors are found that are could cause confusion, these will then be rejected to avoid misleading results.

The majority of these errors will be descriptive.
Here are a few examples of this kind of error:

### "Cannot parse the name and length in the LOCUS line"

This will occur when the record identifier in the `LOCUS` line of a genbank file contains spaces or merges with the record length.

Ensure that the `LOCUS` line is correctly formatted and all fields are present.

### "'ascii' codec can't encode characters in position ..."

This occurs when the input file is corrupted or uses a unusual character set.

Remove any characters not in the "ascii" or "UTF-8" character sets.

### "Premature end of line during sequence data"

This occurs in GBK files when the record terminator `//` is missing.
The usual cause is downloads from the NCBI not completing correctly,
but can also occur when manually editing files.
