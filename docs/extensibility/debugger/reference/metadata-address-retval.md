---
title: "METADATA_ADDRESS_RETVAL |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4de62d86bcb8453c4bdd01fc697390d1c55d9dd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
この構造体は、メソッドまたは関数から戻り値を表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## <a name="terms"></a>用語  
 tokMethod  
 この戻り値が、メソッドの ID。  
  
 dwCorType  
 戻り値の基本型。 これは、値から、`CorElementType`列挙で定義されている、 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK corhdr.h ファイル。  
  
 dwSigSize  
 戻り値の署名のサイズ (に格納されている`rgSig`)。  
  
 rgSig  
 戻り値の署名を形成するバイトの配列。  
  
## <a name="remarks"></a>コメント  
 この構造体の共用体の一部である、 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)ときに構造体、`dwKind`のフィールド、`DEBUG_ADDRESS_UNION`構造に設定されている`ADDRESS_KIND_RETVAL`(から値、 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列挙体)。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)