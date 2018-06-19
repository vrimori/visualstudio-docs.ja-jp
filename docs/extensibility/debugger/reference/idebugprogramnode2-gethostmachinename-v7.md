---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2adc7125c79afc6b9ebc16b6c4b36f5c147bcdfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115396"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> 推奨されなくなりました。 使用しないでください。

## <a name="syntax"></a>構文

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

#### <a name="parameters"></a>パラメーター

`pbstrHostMachineName`  
[out]プログラムが実行されているコンピューターの名前を返します。

## <a name="return-value"></a>戻り値

実装を常に返します`E_NOTIMPL`です。

## <a name="remarks"></a>コメント

> [!WARNING]
> Visual Studio 2005 の時点でこのメソッドは使用されなくを常に返す必要があります`E_NOTIMPL`です。

## <a name="see-also"></a>関連項目

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)