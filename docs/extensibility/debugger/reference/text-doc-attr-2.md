---
title: TEXT_DOC_ATTR_2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d74bbfa4fb89baf01c5fb3d49a0767c67b800ce
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872727"
---
# <a name="textdocattr2"></a>TEXT_DOC_ATTR_2
ドキュメントの属性について説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef DWORD TEXT_DOC_ATTR_2;  
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
```csharp  
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
## <a name="members"></a>メンバー  
 TEXT_DOC_ATTR_READONLY_2  
 文書が読み取り専用であることを示します。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  C# のアセンブリに、この値が実際に定義されていません。 代わりに、ソース ファイルに定義をコピーする必要があります。  
  
 引数として渡される、 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)