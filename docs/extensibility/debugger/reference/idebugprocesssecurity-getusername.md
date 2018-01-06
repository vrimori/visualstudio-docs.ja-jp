---
title: "IDebugProcessSecurity::GetUserName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: aa8da8828dbbc314ce976572d1f6bd9d5abf5721
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
ポートのサプライヤーからユーザー名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 [out]ユーザー名を含む文字列。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功したかどうか、それを返します`S_OK`です。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 `GetUserName`表示されるユーザー名を返します、**ユーザー名**の列、**プロセスにアタッチする** ダイアログ ボックス。 表示する、**プロセスにアタッチする**ダイアログ ボックスで、 をクリックして**プロセスにアタッチする**で、**ツール**でメニュー、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。  
  
## <a name="see-also"></a>参照  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)