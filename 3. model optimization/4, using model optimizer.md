# Using the Model Optimizer

`Tensorflow`
1. [Converting a TensorFlow* Model ](https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_convert_model_Convert_Model_From_TensorFlow.html) 
1. [Tensorflow detection model zoo](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md)

`Caffe`
1. [Converting a Caffe* Model](https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_convert_model_Convert_Model_From_Caffe.html)

`Onyx`
1. [Converting a Onyx model](https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_convert_model_Convert_Model_From_ONNX.html)  
1. [Onyx model zoo](https://github.com/onnx/models)

# Cutting Off Parts of a Model 

Sometimes some parts of a model must be removed while the Model Optimizer is converting models to the Intermediate Representation. 
The following examples are the situations when model cutting is useful or even required:

* model has pre- or post-processing parts that cannot be translated to existing Inference Engine layers.

* model has a training part that is convenient to be kept in the model, but not used during inference.

* model is too complex (contains lots of unsupported operations that cannot be easily implemented as custom layers), so the complete model cannot be converted in one shot.

* model is one of the supported SSD models. In this case, you need to cut a post-processing part off.

* problem with model conversion in the Model Optimizer or inference in the Inference Engine occurred. To localize the issue, limit the scope for conversion by iteratively searching for problematic places in the model.

* single custom layer or a combination of custom layers is isolated for debugging purposes.


[follow these documentation steps to remove parts of the model](https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_convert_model_Cutting_Model.html)

# Supported Framework Layers
------- [see documentation here]((https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_Supported_Frameworks_Layers.html))

If a layer is not supported in the inference engine, we have the following options:

* use of custom layers

* running the given unsupported layer in its original framework

* check available extensions that can add support for the layer

documentation  
------- [Custom Layers in the Model Optimizer ](https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_customize_model_optimizer_Customize_Model_Optimizer.html)   
------- [TensorFlow operation on a given unsupported layer](https://docs.openvinotoolkit.org/latest/_docs_MO_DG_prepare_model_customize_model_optimizer_Offloading_Sub_Graph_Inference.html)