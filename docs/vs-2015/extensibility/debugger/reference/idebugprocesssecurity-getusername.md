---
title: IDebugProcessSecurity::GetUserName |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0dee5cd71cc41c8377914ade5800976d9e7ff57
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547936"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugProcessSecurity::GetUserName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity-getusername)します。  
  
ポート サプライヤーからユーザー名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrUserName`  
 [out]ユーザー名を表す文字列。  
  
## <a name="return-value"></a>戻り値  
 返します、メソッドが成功したかどうかは`S_OK`します。 それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 `GetUserName` 表示されるユーザー名を返します、**ユーザー名**の列、**プロセスにアタッチ** ダイアログ ボックス。 表示する、**プロセスにアタッチ**ダイアログ ボックスで、をクリックして**プロセスにアタッチ**で、**ツール**でメニュー、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]統合開発環境 (IDE)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

