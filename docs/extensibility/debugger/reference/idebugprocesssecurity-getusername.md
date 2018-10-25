---
title: IDebugProcessSecurity::GetUserName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f13d7597877104613f0e6ef6380abf0b6bc2a594
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891471"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
ポート サプライヤーからユーザー名を取得します。  
  
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
 [out]ユーザー名を表す文字列。  
  
## <a name="return-value"></a>戻り値  
 返します、メソッドが成功したかどうかは`S_OK`します。 それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 `GetUserName` 表示されるユーザー名を返します、**ユーザー名**の列、**プロセスにアタッチ** ダイアログ ボックス。 表示する、**プロセスにアタッチ**ダイアログ ボックスで、をクリックして**プロセスにアタッチ**で、**ツール**でメニュー、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE)。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)