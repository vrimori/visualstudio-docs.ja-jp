---
title: JsRunSerializedScriptWithCallback 関数 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0608d778-f65b-4dc5-a745-364aac57ef59
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce51c9473100e71831dd53cc6572d9740790ffa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568862"
---
# <a name="jsrunserializedscriptwithcallback-function"></a>JsRunSerializedScriptWithCallback 関数
シリアル化されたスクリプトを実行します。     必要な場合のみ、スクリプト ソースの遅延読み込みを行う機能を提供します。  
  
## <a name="syntax"></a>構文  
  
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
  
#### <a name="parameters"></a>パラメーター  
 `scriptLoadCallback`  
 スクリプトのソース コードを読み込む必要がある場合に呼び出されるコールバック。  
  
 `scriptUnloadCallback`  
 シリアル化されたスクリプトとソース コードが不要になると呼び出されるコールバック。  
  
 `buffer`  
 シリアル化されたスクリプト。  
  
 `sourceContext`  
 デバッグ可能なスクリプト コンテキストで使用できるスクリプトを識別するクッキー。     このコンテキストは、scriptLoadCallback と scriptUnloadCallback に渡されます。  
  
 `sourceUrl`  
 スクリプトの元の場所。  
  
 `result`  
 スクリプトを実行した結果 (存在する場合)。 このパラメーターには、null を指定できます。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  この API は、ストア アプリにはまだ使用できません。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
 ランタイムは、バッファーから作成されたすべての関数のすべてのインスタンスがガベージ コレクションされるまでバッファーを保持します。  その後、解放しても安全であることを呼び出し元に通知するために、scriptUnloadCallback を呼び出します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)