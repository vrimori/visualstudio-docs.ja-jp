---
title: IDebugProgramNode2::Attach_V7 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0e7726786d3488cc4578dbc6efd016510a3d52d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935438"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> 非推奨とされます。 使用しないでください。

## <a name="syntax"></a>構文

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

#### <a name="parameters"></a>パラメーター

`pMDMProgram` [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)にアタッチするプログラムを表すインターフェイスです。

 `pCallback` [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM にデバッグ イベントを送信するためのインターフェイス。

 `dwReason` [in]値、 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)アタッチの理由を指定する列挙体。

## <a name="return-value"></a>戻り値

実装は常に返す必要があります`E_NOTIMPL`します。

## <a name="remarks"></a>Remarks

> [!WARNING]
> Visual Studio 2005 の時点でこのメソッドは使用されなくと常に返す必要があります`E_NOTIMPL`します。 参照してください、 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)プログラム ノードにアタッチできないことを示す必要がある場合、または、[プログラム] ノードは、プログラムを設定するだけの場合、その他の方法のためのインターフェイス`GUID`します。 それ以外の場合、実装、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッド。

## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005 より前

このメソッドは、DE がデバッグ中のプログラムのアドレス空間で実行する場合にのみ実装する必要があります。 このメソッドが返す必要がありますそれ以外の場合、`S_FALSE`します。

このメソッドが呼び出されたときに、DE を送信する必要があります、 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)イベント オブジェクトのこのインスタンスに既に送信されていない場合、 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)インターフェイスだけでなく[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)と[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)イベント オブジェクト。 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)場合にイベント オブジェクトを送信し、`dwReason`パラメーターが`ATTACH_REASON_LAUNCH`します。

呼び出す必要があります、DE、 [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)メソッドを[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)で指定されたオブジェクト、 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)イベント オブジェクト、およびそのアプリケーションの GUID を格納する必要がありますインスタンス データで、 `IDebugProgram2` DE で実装されるオブジェクト。

## <a name="see-also"></a>関連項目

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)  
[添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)  
[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)  
[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)