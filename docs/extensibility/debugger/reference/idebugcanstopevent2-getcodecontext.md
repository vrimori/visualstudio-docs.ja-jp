---
title: IDebugCanStopEvent2::GetCodeContext |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetCodeContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetCodeContext
ms.assetid: eecf08b6-f9b7-4358-941b-3a448a92ac62
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05cd4729635042d67f063bbba412c19a4a2f89f7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818342"
---
# <a name="idebugcanstopevent2getcodecontext"></a>IDebugCanStopEvent2::GetCodeContext
このイベントの場所を記述したコードのコンテキストを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCodeContext(   
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppCodeContext`  
 [out]返します、 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)コードの現在の場所を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ほとんどのランタイム アーキテクチャ、コードのコンテキストを特定の命令を指すプログラムの実行のストリーム内のアドレスとして考えることができます。  
  
 ソース コードの行指向は、ドキュメントのコンテキストを取得する、 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)