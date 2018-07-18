---
title: JsErrorCode 列挙型 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsErrorCode
helpviewer_keywords:
- JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569092"
---
# <a name="jserrorcode-enumeration"></a>JsErrorCode 列挙型
Chakra ホスト API から返されたエラー コード。  
  
## <a name="syntax"></a>構文  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>メンバー  
  
### <a name="values"></a>値  
  
|名前|説明|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|コンテキストは、既にデバッグ状態であるので、デバッグ状態にすることはできません。|  
|`JsErrorAlreadyProfilingContext`|コンテキストは既にプロファイル中であるため、プロファイルを開始できません。|  
|`JsErrorArgumentNotObject`|オブジェクト値を操作するホスト API がオブジェクト以外の値により呼び出されました。|  
|`JsErrorBadSerializedScript`|不適切なシリアル化スクリプトが使用されたか、シリアル化されたスクリプトが別のバージョンの Chakra エンジンによってシリアル化されました。|  
|`JsErrorCannotDisableExecution`|ランタイムは信頼できるスクリプトの中断をサポートしていません。|  
|`JsErrorCannotSerializeDebugScript`|スクリプトはデバッグ コンテキストでシリアル化できません。|  
|`JsErrorCategoryEngine`|エンジン自体に発生したエラーに関連するカテゴリ。|  
|`JsErrorCategoryFatal`|致命的なエンジンの失敗を示すエラー カテゴリ。|  
|`JsErrorCategoryScript`|スクリプトのエラーに関連するエラー カテゴリ。|  
|`JsErrorCategoryUsage`|API 自体の不適切な使用に関連するエラー カテゴリ。|  
|`JsErrorFatal`|エンジンに致命的なエラーが発生しました。|  
|`JsErrorHeapEnumInProgress`|スクリプト コンテキストでヒープ列挙が現在進行中です。|  
|`JsErrorIdleNotEnabled`|ホストがアイドル プロセスを有効にしなかったときに指定されるアイドル通知。|  
|`JsErrorInDisabledState`|ランタイムは無効な状態です。|  
|`JsErrorInExceptionState`|エンジンは例外状態であり、例外がクリアされるまで API を呼び出すことはできません。|  
|`JsErrorInObjectBeforeCollectCallback`|この操作は、コレクト コールバックの前のオブジェクトではサポートされていません。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
|`JsErrorInProfileCallback`|スクリプト コンテキストは、プロファイルのコールバック中です。|  
|`JsErrorInThreadServiceCallback`|スレッド サービス コールバックは現在進行中です。|  
|`JsErrorInvalidArgument`|ホスト API への引数が無効でした。|  
|`JsErrorNoCurrentContext`|ホスト API では、現在のコンテキストが必要ですが、現在のコンテキストがありません。|  
|`JsErrorNotImplemented`|ホスト API がまだ実装されていません。|  
|`JsErrorNullArgument`|ホスト API の引数は、null が許可されないコンテキストで null でした。|  
|`JsErrorObjectNotInspectable`|オブジェクトを `IInspectable` ポインターにラップ解除できません。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
|`JsErrorOutOfMemory`|Chakra エンジンでメモリが不足しています。|  
|`JsErrorPropertyNotSymbol`|シンボル プロパティ ID で機能するのに、非シンボル プロパティ ID で呼び出されたホスティング ID。関数が非シンボル プロパティ ID で呼び出される場合、エラー コードが `JsGetSymbolFromPropertyId` によって返されます。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
|`JsErrorPropertyNotString`|文字列プロパティ ID で機能するのに、非文字列プロパティ ID で呼び出されたホスティング ID。関数が非文字列プロパティ ID で呼び出される場合、エラー コードが既存の `JsGetPropertyNamefromId` によって返されます。<br /><br /> この列挙値は、エッジ モードでのみサポートされています。|  
|`JsErrorRuntimeInUse`|まだ使用中のランタイムは破棄できません。|  
|`JsErrorScriptCompile`|JavaScript のコンパイルに失敗しました。|  
|`JsErrorScriptEvalDisabled`|スクリプトは、 `eval` または `function` を使用しようとしましたが eval が無効であったために終了しました。|  
|`JsErrorScriptException`|スクリプトの実行中に JavaScript 例外が発生しました。|  
|`JsErrorScriptTerminated`|スクリプトは、ランタイムの中断要求により終了しました。|  
|`JsErrorWrongRuntime`|ホスト API は、別の JavaScript ランタイムで作成されたオブジェクトで呼び出されました。|  
|`JsErrorWrongThread`|ホスト API は、正しくないスレッドで呼び出されました。|  
|`JsNoError`|成功エラー コードです。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)