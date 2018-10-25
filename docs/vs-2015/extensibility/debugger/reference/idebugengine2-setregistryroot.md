---
title: IDebugEngine2::SetRegistryRoot |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7e6f68f00570590715955f661679a56a7533e4b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919690"
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

デバッグ エンジン (DE) のレジストリ ルートを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszRegistryRoot`  
 [in]使用するレジストリ ルート。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 この方法により、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]デが; のレジストリ設定の取得に使用する別のレジストリ ルートを指定する"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp"など。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

