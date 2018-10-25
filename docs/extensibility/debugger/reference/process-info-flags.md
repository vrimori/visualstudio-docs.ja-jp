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
ms.openlocfilehash: 04bc34de6e7ecbc438cfc63ed08c684cf4224366
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917025"
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

Namespace: Microsoft.VisualStudio.Debugger.Interop

アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>関連項目

[列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)