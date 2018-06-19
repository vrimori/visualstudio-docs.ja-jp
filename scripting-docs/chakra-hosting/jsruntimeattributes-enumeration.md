---
title: JsRuntimeAttributes 列挙型 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsRuntimeAttributes
helpviewer_keywords:
- JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569062"
---
# <a name="jsruntimeattributes-enumeration"></a>JsRuntimeAttributes 列挙型
ランタイムの属性。  
  
## <a name="syntax"></a>構文  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="values"></a>値  
  
|名前|説明|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|ランタイムは、信頼できるスクリプトの中断をサポートする必要があります。 これによって、実行時のパフォーマンスが若干低下しますが、スクリプトの中断要求をチェックする箇所が増えます。|  
|`JsRuntimeAttributeDisableBackgroundWork`|ランタイムは、バックグラウンド スレッド上で (ガベージ コレクションなどの) 処理を行いません。|  
|`JsRuntimeAttributeDisableEval`|`eval` か `function` のコンストラクターを使用すると、例外がスローされます。|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|ランタイムは、ネイティブ コードを生成しません。|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|ランタイムは、すべての実験用の機能を有効にします。|  
|`JsRuntimeAttributeEnableIdleProcessing`|ホストは、 `JsIdle`を呼び出すため、アイドル プロセスを有効にします。 それ以外の場合、ランタイムはメモリを若干積極的に管理します。|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|`JsSetException` を呼び出すと、スクリプト デバッガーの例外もディスパッチされ (存在する場合)、デバッガーは例外を中断する機会を与えられます。|  
|`JsRuntimeAttributeNone`|特別な属性はありません。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)