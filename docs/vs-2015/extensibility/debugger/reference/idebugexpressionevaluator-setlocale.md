---
title: IDebugExpressionEvaluator::SetLocale |Microsoft Docs
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
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c2f714f32109848d3cacf7d74ed1fa6a064cb07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761758"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、印刷可能な結果の作成に使用する言語を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wLangID`  
 [in]言語識別子です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 EE は、実行時に言語を変更することである必要がありますので、式エバリュエーター (EE) が読み込まれる間により、このメソッドに何度もを呼び出すことがあります。 EE では、このロケールを使用して、適切な言語でエラー メッセージ、および文字列を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)

