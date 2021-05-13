# Upload Output to S3

This example shows a tekton pipeline that supports a common scenario: 

Upload artifacts to S3 when pipeline is finished.

## The Usual Approach

The usual approach towards accomplishing this would be to include a task in your pipeline 
that manually uploads the files to S3. For example, by using the [aws-cli](https://hub.tekton.dev/tekton/task/aws-cli) task from Tekton Hub.  

## This 🎩 Approach

This example, instead, uses: 

* A pipeline,
* with a single task that uses a [Storage PipelineResource](https://github.com/tektoncd/pipeline/blob/main/docs/resources.md#storage-resource)
* the task then writes a file in the right path,
* 🎉 the files are uploaded to S3 !!


## Secret

2 examples are provided: 

* a standard Secret, that embeds the necessary `boto_config` values
* a SecretDefinition, in case you're working with [tuenti/secrets-manager](https://github.com/tuenti/secrets-manager) and Hashicorp Vault. 
