---
title: IDebugPortSupplierDescription2::GetDescription |Microsoft Docs
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
- IDebugPortSupplierDescription2::GetDescription
ms.assetid: bff5f536-1cd1-4313-8856-db7b05818305
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14b50a469680d1263c57321d2649501e129d3d02
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539221"
---
# <a name="idebugportsupplierdescription2getdescription"></a>IDebugPortSupplierDescription2::GetDescription
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugPortSupplierDescription2::GetDescription](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplierdescription2-getdescription)します。  
  
ポート サプライヤーの説明と記述メタデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetDescription(  
   PORT_SUPPLIER_DESCRIPTION_FLAGS *pdwFlags,  
   BSTR *pbstrText  
);  
```  
  
```csharp  
public int GetDescription(  
   out enum_PORT_SUPPLIER_DESCRIPTION_FLAGS pdwFlags,  
   out string pbstrText  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwFlags`  
 [out]メタデータの説明のフラグを設定します。  
  
 `pbstrText`  
 [out]ポート サプライヤーの説明です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)

