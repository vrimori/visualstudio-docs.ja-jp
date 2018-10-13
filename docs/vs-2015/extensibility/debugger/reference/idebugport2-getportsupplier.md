---
title: IDebugPort2::GetPortSupplier |Microsoft Docs
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
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 7a7b0615-df6b-4726-ab35-39dfa1ebed8f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0758b7c2c169a3c5bcea49fa9583489b9cf21b5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281958"
---
# <a name="idebugport2getportsupplier"></a>IDebugPort2::GetPortSupplier
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このポートのポート サプライヤーを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetPortSupplier(   
   IDebugPortSupplier2** ppSupplier  
);  
```  
  
```csharp  
int GetPortSupplier(   
   out IDebugPortSupplier2 ppSupplier  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppSupplier`  
 [out]返します、 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)オブジェクトは、ポートのポート サプライヤーを表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)

