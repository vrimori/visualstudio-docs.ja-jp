---
title: "GETNAME_TYPE |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GETNAME_TYPE
helpviewer_keywords: GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06cb7cc6e882bbd1539b34035ca5a9be685512e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="getnametype"></a>GETNAME_TYPE
取得するファイルの名前の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 モニカーの形式で、ドキュメントまたはコンテキストの一意の名前を指定します。  
  
 GN_URL  
 ドキュメントまたはコンテキストの URL 名を指定します。  
  
 GN_TITLE  
 1 つが存在する場合は、ドキュメントのタイトルを指定します。  
  
 GN_STARTPAGEURL  
 プロセスの開始ページの URL を取得します。  
  
## <a name="remarks"></a>コメント  
 これらの値がパラメーターとして渡される、 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)、 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)、および[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)メソッド名の種類を指定します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)