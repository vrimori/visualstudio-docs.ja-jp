---
title: IDebugDocumentText2::GetSize |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0c62ca1695de65b005fa839c69cbcc02452f1207
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819668"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
ドキュメントのこの位置でテキストのサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcNumLines`  
 [out]テキスト行の数を返します。  
  
 `pcNumChars`  
 [out]テキストの文字数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 [C++ のみ]特定の値が望ましくない場合は、パラメーターの場合は NULL を渡します。  
  
 [C# のみ]両方のパラメーターを指定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)