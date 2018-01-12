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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5c27588eb6d09c0565b4b4d8faec52239ef792f7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
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
  
  