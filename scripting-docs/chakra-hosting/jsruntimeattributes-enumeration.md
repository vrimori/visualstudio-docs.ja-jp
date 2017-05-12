---
title: "JsRuntimeAttributes 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRuntimeAttributes"
helpviewer_keywords: 
  - "JsRuntimeAttributes 列挙型"
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# JsRuntimeAttributes 列挙型
ランタイムの属性。  
  
## 構文  
  
```  
enum JsRuntimeAttributes;  
```  
  
## メンバー  
  
### 値  
  
|名前|説明|  
|--------|--------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|ランタイムは、信頼できるスクリプトの中断をサポートする必要があります。 これによって、実行時のパフォーマンスが若干低下しますが、スクリプトの中断要求をチェックする箇所が増えます。|  
|`JsRuntimeAttributeDisableBackgroundWork`|ランタイムは、バックグラウンド スレッド上で \(ガベージ コレクションなどの\) 処理を行いません。|  
|`JsRuntimeAttributeDisableEval`|`eval` か `function` のコンストラクターを使用すると、例外がスローされます。|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|ランタイムは、ネイティブ コードを生成しません。|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|ランタイムは、すべての実験用の機能を有効にします。|  
|`JsRuntimeAttributeEnableIdleProcessing`|ホストは、`JsIdle` を呼び出すため、アイドル プロセスを有効にします。 それ以外の場合、ランタイムはメモリを若干積極的に管理します。|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|`JsSetException` を呼び出すと、スクリプト デバッガーの例外もディスパッチされ \(存在する場合\)、デバッガーは例外を中断する機会を与えられます。|  
|`JsRuntimeAttributeNone`|特別な属性はありません。|  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)