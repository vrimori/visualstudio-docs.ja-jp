---
title: GETNAME_TYPE |Microsoft Docs
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
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2607ddd84ead55ed627c72e1c9fd2ec3e280349f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815951"
---
# <a name="getnametype"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得するファイルの名前の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>メンバー  
 GN_NAME  
 ドキュメントまたはコンテキストのフレンドリ名を指定します。  
  
 GN_FILENAME  
 ドキュメントまたはコンテキストの完全なパスを指定します。  
  
 GN_BASENAME  
 ドキュメントまたはコンテキストの完全なパスではなく基本ファイル名を指定します。  
  
 GN_MONIKERNAME  
 モニカーの形式でドキュメントまたはコンテキストの一意の名前を指定します。  
  
 GN_URL  
 ドキュメントまたはコンテキストの URL 名を指定します。  
  
 GN_TITLE  
 存在する場合は、ドキュメントのタイトルを指定します。  
  
 GN_STARTPAGEURL  
 プロセスの開始ページの URL を取得します。  
  
## <a name="remarks"></a>Remarks  
 これらの値をパラメーターとして渡される、 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)、 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)、および[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)メソッド名を返しますの種類を指定します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)

