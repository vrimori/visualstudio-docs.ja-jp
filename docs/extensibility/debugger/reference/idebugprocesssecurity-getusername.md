---
title: "IDebugProcessSecurity::GetUserName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 081f073ba59021ca56dd084bd2cef0fde6c5c32e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
