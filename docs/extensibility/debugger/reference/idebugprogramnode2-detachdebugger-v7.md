---
title: IDebugProgramNode2::DetachDebugger_V7 |Microsoft ドキュメント
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
ms.openlocfilehash: 3a79c073048fe30a4abed069487ad09943253475
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7

> [!Note]
> 推奨されなくなりました。 使用しないでください。

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

実装を常に返します`E_NOTIMPL`です。

## <a name="remarks"></a>コメント

> [!WARNING]
> Visual Studio 2005 の時点でこのメソッドは使用されなくを常に返す必要があります`E_NOTIMPL`です。

このメソッドは、デバッガーが突然終了するときに呼び出されます。 このメソッドが呼び出されたときに、DE は必要があります、ユーザーがそこからデタッチされたものとしてプログラムを再開します。 これ以上のデバッグ イベントを送信する必要があります。 プログラムは、デバッガーの別のインスタンスからアタッチ可能な状態である必要があります。

## <a name="see-also"></a>関連項目

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)