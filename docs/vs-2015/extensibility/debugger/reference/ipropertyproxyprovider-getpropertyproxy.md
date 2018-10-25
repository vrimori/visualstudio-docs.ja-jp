---
title: IPropertyProxyProvider::GetPropertyProxy |Microsoft Docs
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
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f93c6d34e1b1a2998a72bfa9bf4d950f135de176
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815796"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定したプロキシの id プロパティのプロキシ インターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetPropertyProxy(  
   DWORD                  dwID,  
   IPropertyProxyEESide** proxy  
);  
```  
  
```csharp  
int GetPropertyProxy(  
   uint                     dwID,  
   out IPropertyProxyEESide proxy  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwID`  
 [in]必要なプロパティのプロキシの ID。  
  
 `proxy`  
 [out]返します、 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 外部型のビジュアライザーをサポートするために、このメソッド通常転送への呼び出し、 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)メソッド。 参照してください[視覚化してデータの表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)IEEVisualizerService を取得する方法の詳細について。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [データの視覚化と表示](../../../extensibility/debugger/visualizing-and-viewing-data.md)

