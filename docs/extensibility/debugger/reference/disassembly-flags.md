---
title: DISASSEMBLY_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6d42a7c5e9247359abfcdb4d65db5a4e0de247e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916401"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
逆アセンブリのフラグを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## <a name="members"></a>メンバー  
 DF_DOCUMENTCHANGE  
 この命令が別のドキュメントは、前のことを示します。  
  
 DF_DISABLED  
 この命令は実行されないことを示します。  
  
 DF_INSTRUCTION_ACTIVE  
 この命令が実行される次の手順のいずれかであることを示します (あります 1 つ以上)。  
  
 DF_DATA  
 この命令は、データ (コードではなく) で、実際にあることを示します。  
  
 DF_HASSOURCE  
 この命令にソースがあることを示します。 プロファイルまたはガベージ コレクションのコードなどのいくつかの手順では、対応するソースがあるありません。  
  
 DF_DOCUMENT_CHECKSUM  
 示します`bstrDocumentUrl`フィールドには、ドキュメントの URL の後のチェックサム データが含まれています。 「解説」を参照してください、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)チェックサム データを格納する方法の構造体。  
  
## <a name="remarks"></a>Remarks  
 として使用される、`dwFlags`のメンバー、 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)構造体。  
  
 これらのフラグは、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)