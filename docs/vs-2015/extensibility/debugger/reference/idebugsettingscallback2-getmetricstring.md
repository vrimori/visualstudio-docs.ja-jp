---
title: IDebugSettingsCallback2::GetMetricString |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ce471cc3720c00cf1686ce07d60be1434ccf056
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828371"
---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定した名前のメトリックの値の文字列を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetMetricString(  
    LPCWSTR pszType,  
    REFGUID guidSection,  
    LPCWSTR pszMetric,  
    BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetMetricString(  
    string     pszType,  
    ref Guid   guidSection,  
    string     pszMetric,  
    out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszType`  
 [in]メトリックの種類です。  
  
 `guidSection`  
 [in]セクションの一意の識別子。  
  
 `pszMetric`  
 [in]メトリックの名前。  
  
 `pbstrValue`  
 [out]メトリックの値の文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

