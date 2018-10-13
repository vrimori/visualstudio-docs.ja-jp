---
title: ASSEMBLYLOCRESOLUTION |Microsoft Docs
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
- ASSEMBLYLOCRESOLUTION
helpviewer_keywords:
- ASSEMBLYLOCRESOLUTION enumeration
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dd01bbafe21b4a65bfd8e4e4c9b16080210e6a06
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49244882"
---
# <a name="assemblylocresolution"></a>ASSEMBLYLOCRESOLUTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

アセンブリがある場所を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```csharp  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
```  
  
## <a name="members"></a>メンバー  
 ALR_NAME  
 アセンブリは、現在の名前空間にあります。  
  
 ALR_USERDIR  
 アセンブリは、ユーザー ディレクトリ内にあります。  
  
 ALR_SHAREDDIR  
 アセンブリは共有ディレクトリにあります。  
  
 ALR_REMOTEDIR  
 アセンブリは、リモート ディレクトリ内にあります。  
  
## <a name="remarks"></a>Remarks  
 これらの値がによって返される、 [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)と[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)メソッド。  
  
 これらの値と組み合わせることができます、`OR`操作。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)   
 [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)

