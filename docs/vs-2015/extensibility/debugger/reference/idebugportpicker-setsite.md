---
title: IDebugPortPicker::SetSite |Microsoft Docs
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
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57f3ada6c5a1b2434e5b88b077f71c678321db68
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537688"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugPortPicker::SetSite](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker-setsite)します。  
  
サービス プロバイダーを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSP`  
 [in]サービス プロバイダーのインターフェイスへの参照。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが、他のメソッドが呼び出される前に呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)

