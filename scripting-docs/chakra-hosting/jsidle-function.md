---
title: "JsIdle 関数 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsIdle
helpviewer_keywords: JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="jsidle-function"></a>JsIdle 関数
必要なアイドル プロセスを行うようにランタイムに指示します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `nextIdleTick`  
 さらにアイドル処理が存在する場合の次のシステム タイマー刻み。 null を使用できます。 以降のアイドル処理がない場合はタイマー刻みの最大数を返します。  
  
## <a name="return-value"></a>戻り値  
 操作が成功した場合はコード `JsNoError` 、操作が失敗した場合はエラー コード。  
  
## <a name="remarks"></a>コメント  
 現在のランタイムでアイドル プロセスが有効である場合、呼び出し元の `JsIdle` はホストがアイドルであり、ランタイムがメモリ クリーンアップ タスクを実行できることを現在のランタイムに通知します。  
  
 `JsIdle` はまた、ランタイムにさらにアイドル作業が発生するまでのシステム タイマー刻みの数を返すことができます。 このタイマー刻みの数が経過する前に `JsIdle` を呼び出しても、処理は行われません。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)