---
title: METADATA_TYPE |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66a1632198a0af5490e66a843458fc55bcad2d6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134722"
---
# <a name="metadatatype"></a>METADATA_TYPE
この構造体では、メタデータから取得されたフィールドの種類に関する情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 ulAppDomainID  
 シンボルが元のアプリケーションの ID。 これについては、アプリケーションのインスタンスを一意に識別に使用します。  
  
 guidModule  
 このフィールドを含むモジュールの GUID です。  
  
 tokClass  
 この型のメタデータ トークン ID。  
  
 [C++]`_mdToken`は、 `typedef` 32 ビット`int`です。  
  
## <a name="remarks"></a>コメント  
 この構造体がの共用体の一部として表示されます、 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)ときに構造体、`dwKind`のフィールド、`TYPE_INFO`構造に設定されている`TYPE_KIND_METADATA`(から値、 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)列挙体)。  
  
 `tokClass`値は、型を一意に識別するメタデータ トークン。 メタデータ トークン ID の上位ビットを解釈する方法の詳細については、次を参照してください。、 `CorTokenType` corhdr.h ファイルで列挙、 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)