---
title: "JsRunSerializedScriptWithCallback 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsRunSerializedScriptWithCallback 関数
シリアル化されたスクリプトを実行します。 必要な場合のみ、スクリプト ソースの遅延読み込みを行う機能を提供します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsRunSerializedScriptWithCallback(  
  _In_ JsSerializedScriptLoadSourceCallback scriptLoadCallback,  
  _In_ JsSerializedScriptUnloadCallback scriptUnloadCallback,  
  _In_ BYTE *buffer,  
  _In_ JsSourceContext sourceContext,  
  _In_z_ const wchar_t *sourceUrl,  
  _Out_opt_ JsValueRef *result  
);  
  
```  
  
#### パラメーター  
 `scriptLoadCallback`  
 スクリプトのソース コードを読み込む必要がある場合に呼び出されるコールバック。  
  
 `scriptUnloadCallback`  
 シリアル化されたスクリプトとソース コードが不要になると呼び出されるコールバック。  
  
 `buffer`  
 シリアル化されたスクリプト。  
  
 `sourceContext`  
 デバッグ可能なスクリプト コンテキストで使用できるスクリプトを識別するクッキー。 このコンテキストは、scriptLoadCallback と scriptUnloadCallback に渡されます。  
  
 `sourceUrl`  
 スクリプトの元の場所。  
  
 `result`  
 スクリプトを実行した結果 \(存在する場合\)。 このパラメーターには、null を指定できます。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
  
> [!NOTE]
>  この API は、ストア アプリにはまだ使用できません。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
 ランタイムは、バッファーから作成されたすべての関数のすべてのインスタンスがガベージ コレクションされるまでバッファーを保持します。  その後、解放しても安全であることを呼び出し元に通知するために、scriptUnloadCallback を呼び出します。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)