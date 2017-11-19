---
title: "SetWefProcessId メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0821c799a4d6385997704724c00a2aff4669eb17
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="setwefprocessid-method"></a>SetWefProcessId メソッド
  Web 拡張機能フレームワーク (WEF) のコンテンツを実行しているプロセス id を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*dwProcessId*|WEF コンテンツを実行するために使用するプロセスの識別子です。|  
  
## <a name="return-value"></a>戻り値  
 メソッドが正常に完了したかどうかを示す HRESULT 値。  
  
## <a name="remarks"></a>コメント  
 WEF コンテンツのプロセスの作成後は WEF コンテンツをすべて実行する前に、このメソッドを呼び出す必要があります。  
  
 WEF コンテンツ プロセスにデバッガーをアタッチする開発環境を設定する場合、環境は、このメソッドの実装でこの操作を実行する必要があります。  
  
  