---
title: リファレンス (JavaScript ランタイム) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0bfe50da-fd79-4e00-9458-bc667769b415
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 90b22d51a79bbf6252781a49e2ac6b1749d3674f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24570162"
---
# <a name="reference-javascript-runtime"></a>リファレンス (JavaScript ランタイム)
JavaScript ランタイムの (JsRT) API は、Windows で動作するデスクトップとサーバー側アプリケーションにスクリプト機能を追加します。  
  
 アプリケーションに [ChakraCore](https://github.com/Microsoft/ChakraCore) を埋め込む場合は、代わりに JSRT について [ChakraCore Wiki](http://aka.ms/corejsrtref) を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 ここでは、JsRT ホスト処理をサポートする Typedef、定数、および列挙型について説明します。  
  
-   [JavaScript ランタイムの Typedef、定数、および列挙型](../chakra-hosting/javascript-runtime-typedefs-constants-and-enumerations.md)  
  
 次の関数によって JsRT ホスト処理が可能になります。  
  
-   [JsAddRef 関数](../chakra-hosting/jsaddref-function.md)  
  
-   [JsBooleanToBool 関数](../chakra-hosting/jsbooleantobool-function.md)  
  
-   [JsBoolToBoolean 関数](../chakra-hosting/jsbooltoboolean-function.md)  
  
-   [JsCallFunction 関数](../chakra-hosting/jscallfunction-function.md)  
  
-   [JsCollectGarbage 関数](../chakra-hosting/jscollectgarbage-function.md)  
  
-   [JsConstructObject 関数](../chakra-hosting/jsconstructobject-function.md)  
  
-   [JsConvertValueToBoolean 関数](../chakra-hosting/jsconvertvaluetoboolean-function.md)  
  
-   [JsConvertValueToNumber 関数](../chakra-hosting/jsconvertvaluetonumber-function.md)  
  
-   [JsConvertValueToObject 関数](../chakra-hosting/jsconvertvaluetoobject-function.md)  
  
-   [JsConvertValueToString 関数](../chakra-hosting/jsconvertvaluetostring-function.md)  
  
-   [JsCreateArray 関数](../chakra-hosting/jscreatearray-function.md)  
  
-   [JsCreateArrayBuffer 関数](../chakra-hosting/jscreatearraybuffer-function.md)  
  
-   [JsCreateContext 関数](../chakra-hosting/jscreatecontext-function.md)  
  
-   [JsCreateDataView 関数](../chakra-hosting/jscreatedataview-function.md)  
  
-   [JsCreateError 関数](../chakra-hosting/jscreateerror-function.md)  
  
-   [JsCreateExternalArrayBuffer 関数](../chakra-hosting/jscreateexternalarraybuffer-function.md)  
  
-   [JsCreateExternalObject 関数](../chakra-hosting/jscreateexternalobject-function.md)  
  
-   [JsCreateFunction 関数](../chakra-hosting/jscreatefunction-function.md)  
  
-   [JsCreateNamedFunction 関数](../chakra-hosting/jscreatenamedfunction-function.md)  
  
-   [JsCreateObject 関数](../chakra-hosting/jscreateobject-function.md)  
  
-   [JsCreateRangeError 関数](../chakra-hosting/jscreaterangeerror-function.md)  
  
-   [JsCreateReferenceError 関数](../chakra-hosting/jscreatereferenceerror-function.md)  
  
-   [JsCreateRuntime 関数](../chakra-hosting/jscreateruntime-function.md)  
  
-   [JsCreateSymbol 関数](../chakra-hosting/jscreatesymbol-function.md)  
  
-   [JsCreateSyntaxError 関数](../chakra-hosting/jscreatesyntaxerror-function.md)  
  
-   [JsCreateTypeError 関数](../chakra-hosting/jscreatetypeerror-function.md)  
  
-   [JsCreateTypedArray 関数](../chakra-hosting/jscreatetypedarray-function.md)  
  
-   [JsCreateURIError 関数](../chakra-hosting/jscreateurierror-function.md)  
  
-   [JsDefineProperty 関数](../chakra-hosting/jsdefineproperty-function.md)  
  
-   [JsDeleteIndexedProperty 関数](../chakra-hosting/jsdeleteindexedproperty-function.md)  
  
-   [JsDeleteProperty 関数](../chakra-hosting/jsdeleteproperty-function.md)  
  
-   [JsDisableRuntimeExecution 関数](../chakra-hosting/jsdisableruntimeexecution-function.md)  
  
-   [JsDisposeRuntime 関数](../chakra-hosting/jsdisposeruntime-function.md)  
  
-   [JsDoubleToNumber 関数](../chakra-hosting/jsdoubletonumber-function.md)  
  
-   [JsEnableRuntimeExecution 関数](../chakra-hosting/jsenableruntimeexecution-function.md)  
  
-   [JsEnumerateHeap 関数](../chakra-hosting/jsenumerateheap-function.md)  
  
-   [JsEquals 関数](../chakra-hosting/jsequals-function.md)  
  
-   [JsGetAndClearException 関数](../chakra-hosting/jsgetandclearexception-function.md)  
  
-   [JsGetArrayBufferStorage 関数](../chakra-hosting/jsgetarraybufferstorage-function.md)  
  
-   [JsGetContextData 関数](../chakra-hosting/jsgetcontextdata-function.md)  
  
-   [JsGetContextOfObject 関数](../chakra-hosting/jsgetcontextofobject-function.md)  
  
-   [JsGetCurrentContext 関数](../chakra-hosting/jsgetcurrentcontext-function.md)  
  
-   [JsGetDataViewStorage 関数](../chakra-hosting/jsgetdataviewstorage-function.md)  
  
-   [JsGetExtensionAllowed 関数](../chakra-hosting/jsgetextensionallowed-function.md)  
  
-   [JsGetExternalData 関数](../chakra-hosting/jsgetexternaldata-function.md)  
  
-   [JsGetFalseValue 関数](../chakra-hosting/jsgetfalsevalue-function.md)  
  
-   [JsGetGlobalObject 関数](../chakra-hosting/jsgetglobalobject-function.md)  
  
-   [JsGetIndexedPropertiesExternalData 関数](../chakra-hosting/jsgetindexedpropertiesexternaldata-function.md)  
  
-   [JsGetIndexedProperty 関数](../chakra-hosting/jsgetindexedproperty-function.md)  
  
-   [JsGetNullValue 関数](../chakra-hosting/jsgetnullvalue-function.md)  
  
-   [JsGetOwnPropertyDescriptor 関数](../chakra-hosting/jsgetownpropertydescriptor-function.md)  
  
-   [JsGetOwnPropertyNames 関数](../chakra-hosting/jsgetownpropertynames-function.md)  
  
-   [JsGetOwnPropertySymbols 関数](../chakra-hosting/jsgetownpropertysymbols-function.md)  
  
-   [JsGetProperty 関数](../chakra-hosting/jsgetproperty-function.md)  
  
-   [JsGetPropertyIdFromName 関数](../chakra-hosting/jsgetpropertyidfromname-function.md)  
  
-   [JsGetPropertyIdFromSymbol 関数](../chakra-hosting/jsgetpropertyidfromsymbol-function.md)  
  
-   [JsGetPropertyIdType 関数](../chakra-hosting/jsgetpropertyidtype-function.md)  
  
-   [JsGetPropertyNameFromId 関数](../chakra-hosting/jsgetpropertynamefromid-function.md)  
  
-   [JsGetPrototype 関数](../chakra-hosting/jsgetprototype-function.md)  
  
-   [JsGetRuntime 関数](../chakra-hosting/jsgetruntime-function.md)  
  
-   [JsGetRuntimeMemoryLimit 関数](../chakra-hosting/jsgetruntimememorylimit-function.md)  
  
-   [JsGetRuntimeMemoryUsage 関数](../chakra-hosting/jsgetruntimememoryusage-function.md)  
  
-   [JsGetStringLength 関数](../chakra-hosting/jsgetstringlength-function.md)  
  
-   [JsGetSymbolFromPropertyId 関数](../chakra-hosting/jsgetsymbolfrompropertyid-function.md)  
  
-   [JsGetTrueValue 関数](../chakra-hosting/jsgettruevalue-function.md)  
  
-   [JsGetTypedArrayInfo 関数](../chakra-hosting/jsgettypedarrayinfo-function.md)  
  
-   [JsGetTypedArrayStorage 関数](../chakra-hosting/jsgettypedarraystorage-function.md)  
  
-   [JsGetUndefinedValue 関数](../chakra-hosting/jsgetundefinedvalue-function.md)  
  
-   [JsGetValueType 関数](../chakra-hosting/jsgetvaluetype-function.md)  
  
-   [JsHasException 関数](../chakra-hosting/jshasexception-function.md)  
  
-   [JsHasExternalData 関数](../chakra-hosting/jshasexternaldata-function.md)  
  
-   [JsHasIndexedPropertiesExternalData 関数](../chakra-hosting/jshasindexedpropertiesexternaldata-function.md)  
  
-   [JsHasIndexedProperty 関数](../chakra-hosting/jshasindexedproperty-function.md)  
  
-   [JsHasProperty 関数](../chakra-hosting/jshasproperty-function.md)  
  
-   [JsIdle 関数](../chakra-hosting/jsidle-function.md)  
  
-   [JsInspectableToObject 関数](../chakra-hosting/jsinspectabletoobject-function.md)  
  
-   [JsInstanceOf 関数](../chakra-hosting/jsinstanceof-function.md)  
  
-   [JsIntToNumber 関数](../chakra-hosting/jsinttonumber-function.md)  
  
-   [JsIsEnumeratingHeap 関数](../chakra-hosting/jsisenumeratingheap-function.md)  
  
-   [JsIsRuntimeExecutionDisabled 関数](../chakra-hosting/jsisruntimeexecutiondisabled-function.md)  
  
-   [JsNumberToDouble 関数](../chakra-hosting/jsnumbertodouble-function.md)  
  
-   [JsNumberToInt 関数](../chakra-hosting/jsnumbertoint-function.md)  
  
-   [JsObjectToInspectable 関数](../chakra-hosting/jsobjecttoinspectable-function.md)  
  
-   [JsParseScript 関数](../chakra-hosting/jsparsescript-function.md)  
  
-   [JsParseSerializedScript 関数](../chakra-hosting/jsparseserializedscript-function.md)  
  
-   [JsParseSerializedScriptWithCallback 関数](../chakra-hosting/jsparseserializedscriptwithcallback-function.md)  
  
-   [JsPointerToString 関数](../chakra-hosting/jspointertostring-function.md)  
  
-   [JsPreventExtension 関数](../chakra-hosting/jspreventextension-function.md)  
  
-   [JsProjectWinRTNamespace 関数](../chakra-hosting/jsprojectwinrtnamespace-function.md)  
  
-   [JsRelease 関数](../chakra-hosting/jsrelease-function.md)  
  
-   [JsRunScript 関数](../chakra-hosting/jsrunscript-function.md)  
  
-   [JsRunSerializedScript 関数](../chakra-hosting/jsrunserializedscript-function.md)  
  
-   [JsRunSerializedScriptWithCallback 関数](../chakra-hosting/jsrunserializedscriptwithcallback-function.md)  
  
-   [JsSerializeScript 関数](../chakra-hosting/jsserializescript-function.md)  
  
-   [JsSetContextData 関数](../chakra-hosting/jssetcontextdata-function.md)  
  
-   [JsSetCurrentContext 関数](../chakra-hosting/jssetcurrentcontext-function.md)  
  
-   [JsSetException 関数](../chakra-hosting/jssetexception-function.md)  
  
-   [JsSetExternalData 関数](../chakra-hosting/jssetexternaldata-function.md)  
  
-   [JsSetIndexedPropertiesToExternalData 関数](../chakra-hosting/jssetindexedpropertiestoexternaldata-function.md)  
  
-   [JsSetIndexedProperty 関数](../chakra-hosting/jssetindexedproperty-function.md)  
  
-   [JsSetObjectBeforeCollectCallback 関数](../chakra-hosting/jssetobjectbeforecollectcallback-function.md)  
  
-   [JsSetProjectionEnqueueCallback 関数](../chakra-hosting/jssetprojectionenqueuecallback-function.md)  
  
-   [JsSetPromiseContinuationCallback 関数](../chakra-hosting/jssetpromisecontinuationcallback-function.md)  
  
-   [JsSetProperty 関数](../chakra-hosting/jssetproperty-function.md)  
  
-   [JsSetPrototype 関数](../chakra-hosting/jssetprototype-function.md)  
  
-   [JsSetRuntimeBeforeCollectCallback 関数](../chakra-hosting/jssetruntimebeforecollectcallback-function.md)  
  
-   [JsSetRuntimeMemoryAllocationCallback 関数](../chakra-hosting/jssetruntimememoryallocationcallback-function.md)  
  
-   [JsSetRuntimeMemoryLimit 関数](../chakra-hosting/jssetruntimememorylimit-function.md)  
  
-   [JsStartDebugging 関数](../chakra-hosting/jsstartdebugging-function.md)  
  
-   [JsStartProfiling 関数](../chakra-hosting/jsstartprofiling-function.md)  
  
-   [JsStopProfiling 関数](../chakra-hosting/jsstopprofiling-function.md)  
  
-   [JsStrictEquals 関数](../chakra-hosting/jsstrictequals-function.md)  
  
-   [JsStringToPointer 関数](../chakra-hosting/jsstringtopointer-function.md)  
  
-   [JsValueToVariant 関数](../chakra-hosting/jsvaluetovariant-function.md)  
  
-   [JsVariantToValue 関数](../chakra-hosting/jsvarianttovalue-function.md)  
  
## <a name="see-also"></a>関連項目  
 [JavaScript ランタイムのホスト](../chakra-hosting/hosting-the-javascript-runtime.md)   
 [JavaScript ランタイムのホスト処理](../chakra-hosting/javascript-runtime-hosting.md)