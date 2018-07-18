---
title: JsThreadServiceCallback Typedef | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568772"
---
# <a name="jsthreadservicecallback-typedef"></a>JsThreadServiceCallback Typedef
スレッド サービス コールバック。  
  
## <a name="syntax"></a>構文  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 callback  
 バックグラウンド作業項目のコールバック。  
  
 callbackData  
 コールバックに渡すデータ引数。  
  
## <a name="remarks"></a>コメント  
 ホストは、JsCreateRuntime の呼び出し時にバックグラウンド スレッド サービスを指定できます。 指定時には、バックグラウンド作業項目がこのコールバックを使用してホストに渡されます。 ホストは、バックグラウンド作業項目の実行を直ちに開始し、true または false を返す必要があります。そしてランタイムがスレッド内の作業項目を処理します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jsrt.h  
  
## <a name="see-also"></a>関連項目  
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)