---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 0c7d319d2053cfa67bd4e7fe77c68474fceb03a2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896124"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

説明またはプロセスのプロパティを指定します。

## <a name="syntax"></a>構文

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
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
プロセスは、デバッガーによってデバッグされていることを示します。 可能性がある、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッガー、またはに、いくつかその他のデバッガー、WinDbg などを指定する可能性があります。

PIFLAG_PROCESS_STOPPED  
プロセスが停止していることを示します。 有効な場合にのみ`PIFLAG_DEBUGGER_ATTACHED`も指定します。 Visual Studio 2005 以降で利用できます。

PIFLAG_PROCESS_RUNNING  
プロセスが実行されていることを示します。 有効な場合にのみ`PIFLAG_DEBUGGER_ATTACHED`も指定します。 Visual Studio 2005 以降で利用できます。

## <a name="remarks"></a>Remarks

使用、`Flags`のメンバー、 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)構造体。

これらのフラグは、演算と組み合わせることがあります`OR`します。

## <a name="requirements"></a>必要条件

ヘッダー: msdbg.h

名前空間:Microsoft.VisualStudio.Debugger.Interop

アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目

[列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)