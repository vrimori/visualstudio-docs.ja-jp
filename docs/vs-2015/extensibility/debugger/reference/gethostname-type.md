---
title: GETHOSTNAME_TYPE |Microsoft Docs
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
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 845ec1b24125ee21874efda0b19c956d1e055d8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49848411"
---
# <a name="gethostnametype"></a>GETHOSTNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ホスト名の種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
typedef DWORD GETHOSTNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
```  
  
## <a name="members"></a>メンバー  
 GHN_FRIENDLY_NAME  
 ホストのフレンドリ名を指定します。  
  
 GHN_FILE_NAME  
 ホストのファイル名を指定します。  
  
## <a name="remarks"></a>Remarks  
 これらの値が引数として渡される、 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)さまざまな形式でのホスト名を取得します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

