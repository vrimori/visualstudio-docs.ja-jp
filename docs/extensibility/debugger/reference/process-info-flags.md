---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91e4c4648108cdc6afa28f5a5dd8f9bfd46fcf59
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126348"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

説明またはプロセスのプロパティを指定します。

## <a name="syntax"></a>構文

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="members"></a>メンバー

PIFLAG_SYSTEM_PROCESS  
プロセスがシステム プロセスであることを示します。

PIFLAG_DEBUGGER_ATTACHED  
プロセスは、デバッガーによってデバッグされていることを示します。 ある可能性があります、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッガー、またはそれにいくつか他のデバッガー、WinDbg などの可能性があります。

PIFLAG_PROCESS_STOPPED  
プロセスが停止していることを示します。 有効な場合にのみ`PIFLAG_DEBUGGER_ATTACHED`も指定されています。 Visual Studio 2005 以降を使用できます。

PIFLAG_PROCESS_RUNNING  
プロセスが実行されていることを示します。 有効な場合にのみ`PIFLAG_DEBUGGER_ATTACHED`も指定されています。 Visual Studio 2005 以降を使用できます。

## <a name="remarks"></a>コメント

使用、`Flags`のメンバー、 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造体。

これらのフラグは、ビットごとと組み合わせること`OR`です。

## <a name="requirements"></a>要件

ヘッダー: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目

[列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)