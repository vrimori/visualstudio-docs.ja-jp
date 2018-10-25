---
title: IDebugProgramNode2::DetachDebugger_V7 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 20981c744408e8d25e6e851c39532db939c71b2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939959"
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> 非推奨とされます。 使用しないでください。

## <a name="syntax"></a>構文

```cpp
HRESULT DetachDebugger_V7 (
   void 
);
```

```csharp
int DetachDebugger_V7 ();
```

## <a name="return-value"></a>戻り値

実装は常に返す必要があります`E_NOTIMPL`します。

## <a name="remarks"></a>Remarks

> [!WARNING]
> Visual Studio 2005 の時点でこのメソッドは使用されなくと常に返す必要があります`E_NOTIMPL`します。

このメソッドは、デバッガーが突然終了するときに呼び出されます。 ユーザーがそこからデタッチされたものとしてこのメソッドが呼び出されるには、DE でプログラムが再開されます。 デバッグ イベントを送信する必要があります。 プログラムが、デバッガーの別のインスタンスからアタッチ可能な状態でなければなりません。

## <a name="see-also"></a>関連項目

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)