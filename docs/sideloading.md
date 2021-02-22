Loading external results
------------------------

antiSMASH 6.0 has added a specification of a JSON based file format that allows
users to load gene cluster predictions from other tools to be displayed
alongside antiSMASH's own results.

## Concept

Tools like [ClusterFinder](http://dx.doi.org/10.1016/j.cell.2014.06.034) and
[DeepBGC](http://dx.doi.org/10.1093/nar/gkz654) offer machine learning based
predictions of BGCs that can complement antiSMASH's own rule-based approach. To
ensure maximal flexibility, antiSMASH 6.0 has created a JSON specification
defining how results from these external tools can be displayed alongside
antiSMASH's own results.

The full JSON specification can be found in
[antiSMASH's GitHub repository](https://github.com/antismash/antismash/blob/master/antismash/detection/sideloader/schemas/general/schema.json),
but we'll present some examples here.

## Example: Adding extra annotations to the balhimycin gene cluster (NCBI: Y16952.3)

The antiSMASH website uses the balhimycin gene cluster (NCBI: Y16952.3) as the
example input dataset, and we'll use this to add some extra annotations to be
displayed via the external results sideloading feature.

### Tool section

The first part of the JSON file is the mandatory description of the annotating
tool. It contains a tool name, a tool version, a free text description of the
tool, and a string to string mapping of configuration settings. This information
will be used in the antiSMASH results details tab created for the tool's
annotations.

```json
{
  "tool": {
    "name": "Example tool",
    "version": "1.2.3",
    "description": "Example of external result sideloading in antiSMASH",
    "configuration": {
      "verbose": "true",
      "multisetting": [
        "first",
        "second"
      ]
    }
  },
  // annotations go here...
}
```

### Records section

The second part of the JSON file is an array of records that annotations should be
created in. Every record needs a name that matches the record ID of the
antiSMASH record to be annotated. In our example, that is "Y16952.3" for the
balhbalhimycin cluster. Multiple records can be annotated in one JSON file, and
annotations that don't match any records in the antiSMASH results are ignored.

In the record, you can either annotate subregions or protoclusters.
Subregions have more of a purely informative function and can be used to
highlight areas of interest. In the example, a subregion is used to highlight
the genes involved in 3,5-dihydroxyphenylglycine biosynthesis, without affecting
the annotation of this region's biosynthetic capabilities. Sideloaded
protoclusters basically fulfill the same function as in antiSMASH: they label
genes involved in a specific biosynthetic pathway. In the example, a
protocluster is used to label the betahydroxy-tyrosine biosynthetic genes. The
"product" value from the JSON annotation is also added to the region's
biosynthetic capabilities.


```json
{
  // tools description up here
  "records": [
    {
      "name": "Y16952.3",
      "subregions": [
        {
          "start": 60178,
          "end": 64054,
          "label": "dhpg biosynthesis",
          "details": {
            "score": "123"
          }
        }
      ],
      "protoclusters": [
        {
          "core_start": 48610,
          "core_end": 52479,
          "product": "bht",
          "details": {
            "score": "6.5",
            "some_option_name": "no"
          }
        }
      ]
    }
  ]
}
```

### Full example file
```json
{
  "tool": {
    "name": "Example tool",
    "version": "1.2.3",
    "description": "Example of external result sideloading in antiSMASH",
    "configuration": {
      "verbose": "true",
      "multisetting": [
        "first",
        "second"
      ]
    }
  },
  "records": [
    {
      "name": "Y16952.3",
      "subregions": [
        {
          "start": 60178,
          "end": 64054,
          "label": "dhpg biosynthesis",
          "details": {
            "score": "6.5"
          }
        }
      ],
      "protoclusters": [
        {
          "core_start": 48610,
          "core_end": 52479,
          "product": "bht",
          "details": {
            "score": "6.5",
            "some_option_name": "no"
          }
        }
      ]
    }
  ]
}
```
