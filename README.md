## MicroMLP is a micro neural network multilayer perceptron (principally used on ESP32 and [Pycom](http://www.pycom.io) modules)

![HC²](hc2.png "HC²")

Very easy to integrate and very light with one file only :
- `"microMLP.py"`

Use deep learning for :
- Signal processing (speech processing, identification, filtering)
- Image processing (compression, recognition, patterns)
- Control (diagnosis, quality control, robotics)
- Optimization (planning, traffic regulation, finance)
- Simulation (black box simulation)
- Classification (DNA analysis)
- Approximation (unknown function, complex function)

### Using *MicroMLP* static functions :

| Name | Function |
| - | - |
| Create | `mlp = MicroMLP.Create(neuronsByLayers, activateFunctionName, layersAutoConnectFunction=None)` |
| LoadFromFile | `mlp = MicroMLP.LoadFromFile(filename)` |

### Using *MicroMLP* main class :

| Name | Function |
| - | - |
| Constructor | `mlp = MicroMLP(activateFunctionName)` |
| GetLayer | `mlp.GetLayer(layerIndex)` |
| GetLayerIndex | `mlp.GetLayerIndex(layer)` |
| RemoveLayer | `mlp.RemoveLayer(layer)` |
| GetInputLayer | `mlp.GetInputLayer()` |
| GetOutputLayer | `mlp.GetOutputLayer()` |
| Learn | `mlp.Learn(inputVectorNNValues, targetVectorNNValues)` |
| Test | `mlp.Test(inputVectorNNValues, targetVectorNNValues)` |
| Predict | `mlp.GetLayer(inputVectorNNValues)` |
| SaveToFile | `mlp.GetLayer(filename)` |
| AddExample | `mlp.AddExample(inputVectorNNValues, targetVectorNNValues)` |
| ClearExamples | `mlp.ClearExamples()` |
| LearnExamples | `mlp.LearnExamples(timeInSec)` |

| Property | Example | Read/Write |
| - | - | - |
| Layers | `mlp.Layers` | get |
| LayersCount | `mlp.LayersCount` | get |
| ActivateFunctionName | `mlp.ActivateFunctionName` | get |
| IsNetworkComplete | `mlp.IsNetworkComplete` | get |
| MSE | `mlp.MSE` | get |
| MAE | `mlp.MAE` | get |
| MSEPercent | `mlp.MSEPercent` | get |
| MAEPercent | `mlp.MAEPercent` | get |
| ExamplesCount | `mlp.ExamplesCount` | get |

| Variable | Default |
| - | - |
| `'MicroMLP.Eta'` | 0.30 |
| `'MicroMLP.Alpha'` | 0.75 |
| `'MicroMLP.Gain'` | 2.70 |

| Activation function name | Const | Detail |
| - | - | - |
| `'Binary'` | MicroMLP.ACTFUNC_BINARY | Binary step |
| `'Sigmoid'` | MicroMLP.ACTFUNC_SIGMOID | Logistic (sigmoid or soft step) |
| `'Tanh'` | MicroMLP.ACTFUNC_TANH | Hyperbolic tangent |
| `'ReLU'` | MicroMLP.ACTFUNC_RELU | Rectified linear unit |
| `'Gaussian'` | MicroMLP.ACTFUNC_GAUSSIAN | Gaussian function |

| Layers auto-connect function | Detail |
| - | - |
| `MicroMLP.LayersFullConnect` | Network fully connected |

### Using *MicroMLP.Layer* class :

| Name | Function |
| - | - |
| Constructor | `layer = MicroMLP.Layer(parentMicroMLP, neuronsCount=0, activateFunctionName=None)` |
| GetLayerIndex | `layer.GetLayerIndex()` |
| GetNeuron | `layer.GetNeuron(neuronIndex)` |
| GetNeuronIndex | `layer.GetNeuronIndex(neuron)` |
| AddNeuron | `layer.AddNeuron(neuron)` |
| RemoveNeuron | `layer.RemoveNeuron(neuron)` |
| ComputeLayerValues | `layer.ComputeLayerValues()` |
| ComputeLayerErrors | `layer.ComputeLayerErrors(training=False)` |
| GetMeanSquareError | `layer.GetMeanSquareError()` |
| GetMeanAbsoluteError | `layer.GetMeanAbsoluteError()` |
| GetMeanSquareErrorAsPercent | `layer.GetMeanSquareErrorAsPercent()` |
| GetMeanAbsoluteErrorAsPercent | `layer.GetMeanAbsoluteErrorAsPercent()` |
| Remove | `layer.Remove()` |

| Property | Example | Read/Write |
| - | - | - |
| ParentMicroMLP | `layer.ParentMicroMLP` | get |
| ActivateFunctionName | `layer.ActivateFunctionName` | get |
| Neurons | `layer.Neurons` | get |
| NeuronsCount | `layer.NeuronsCount` | get |

### Using *MicroMLP.InputLayer(Layer)* class :

| Name | Function |
| - | - |
| Constructor | `inputLayer = MicroMLP.InputLayer(parentMicroMLP, neuronsCount=0)` |
| SetInputVectorNNValues | `inputLayer.SetInputVectorNNValues(inputVectorNNValues)` |

### Using *MicroMLP.OutputLayer(Layer)* class :

| Name | Function |
| - | - |
| Constructor | `outputLayer = MicroMLP.OutputLayer(parentMicroMLP, neuronsCount=0, activateFunctionName=None)` |
| GetOutputVectorValues | `outputLayer.GetOutputVectorValues()` |
| ComputeTargetLayerError | `outputLayer.ComputeTargetLayerError(targetVectorNNValues)` |

### Using *MicroMLP.Neuron* class :

| Name | Function |
| - | - |
| Constructor | `neuron = MicroMLP.Neuron(parentLayer, activateFunctionName)` |
| GetNeuronIndex | `neuron.GetNeuronIndex()` |
| GetInputConnections | `neuron.GetInputConnections()` |
| GetOutputConnections | `neuron.GetOutputConnections()` |
| AddInputConnection | `neuron.AddInputConnection(connection)` |
| AddOutputConnection | `neuron.AddOutputConnection(connection)` |
| RemoveInputConnection | `neuron.RemoveInputConnection(connection)` |
| RemoveOutputConnection | `neuron.RemoveOutputConnection(connection)` |
| SetComputedNNValue | `neuron.SetComputedNNValue(nnvalue)` |
| ComputeValue | `neuron.ComputeValue()` |
| ApplyError | `neuron.ApplyError(deltaError)` |
| ComputeError | `neuron.ComputeError(training=False)` |
| Remove | `neuron.Remove()` |

| Property | Example | Read/Write |
| - | - | - |
| ParentLayer | `neuron.ParentLayer` | get |
| ActivateFunctionName | `neuron.ActivateFunctionName` | get |
| ComputedValue | `neuron.ComputedValue` | get |
| ComputedError | `neuron.ComputedError` | get |
| ComputedDeltaError | `neuron.ComputedDeltaError` | get |

### Using *MicroMLP.Connection* class :

| Name | Function |
| - | - |
| Constructor | `connection = MicroMLP.Connection(neuronSrc, neuronDst, weight=None)` |
| ComputeWeight | `connection.ComputeWeight(eta, alpha)` |
| Remove | `connection.Remove()` |

| Property | Example | Read/Write |
| - | - | - |
| NeuronSrc | `connection.NeuronSrc` | get |
| NeuronDst | `connection.NeuronDst` | get |
| Weight | `connection.Weight` | get |

### Using *MicroMLP.NNValue* static functions :

| Name | Function |
| - | - |
| FromPercent | `nnvalue = MicroMLP.NNValue.FromPercent(value)` |
| NewPercent | `nnvalue = MicroMLP.NNValue.NewPercent()` |
| FromByte | `nnvalue = MicroMLP.NNValue.FromByte(value)` |
| NewByte | `nnvalue = MicroMLP.NNValue.NewByte()` |
| FromBool | `nnvalue = MicroMLP.NNValue.FromBool(value)` |
| NewBool | `nnvalue = MicroMLP.NNValue.NewBool()` |
| FromAnalogSignal | `nnvalue = MicroMLP.NNValue.FromAnalogSignal(value)` |
| NewAnalogSignal | `nnvalue = MicroMLP.NNValue.NewAnalogSignal()` |

### Using *MicroMLP.NNValue* class :

| Name | Function |
| - | - |
| Constructor | `nnvalue = MicroMLP.NNValue(minValue, maxValue, value)` |

| Property | Example | Read/Write |
| - | - | - |
| AsFloat | `nnvalue.AsFloat` | get / set |
| AsInt | `nnvalue.AsInt` | get / set |
| AsPercent | `nnvalue.AsPercent` | get / set |
| AsByte | `nnvalue.AsByte` | get / set |
| AsBool | `nnvalue.AsBool` | get / set |
| AsAnalogSignal | `nnvalue.AsAnalogSignal` | get / set |



### By JC`zic for [HC²](https://www.hc2.fr) ;')

*Keep it simple, stupid* :+1:
