---
title: IDebugExpressionEvaluator::SetLocale |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9c5e1fc300a150b15acc48f12dc3b8c6c01e277
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882647"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
このメソッドは、印刷可能な結果の作成に使用する言語を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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