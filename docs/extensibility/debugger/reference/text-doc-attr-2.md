---
title: "TEXT_DOC_ATTR_2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2c9e498a3f1ea619369694d4caf2d53b3b6d3320
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  アセンブリの C# の場合、この値が実際に定義されていません。 代わりに、ソース ファイルに定義をコピーする必要があります。  
  
 引数として渡される、 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)メソッドです。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)