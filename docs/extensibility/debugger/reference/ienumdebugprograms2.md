---
title: IEnumDebugPrograms2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0277c316329e0adb763eb614f6d453a531781c7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877472"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
このインターフェイスは、現在のデバッグ セッションで実行されているプログラムを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、DE、デバッグ中のプログラムの一覧を提供するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 Visual Studio 呼び出し[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)このインターフェイスを取得します。 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) Visual Studio では使用されません。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugPrograms2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|指定された数の列挙体シーケンス内のプログラムを取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|指定された数の列挙体シーケンス内のプログラムをスキップします。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|列挙子では、プログラムの数を取得します。|  
  
## <a name="remarks"></a>Remarks  
 Visual Studio では、このインターフェイスを使用します。  
  
-   設定、**モジュール**ウィンドウ (呼び出して[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)呼び出して[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)各プログラムで)。  
  
-   設定、**プロセスにアタッチ**一覧 (呼び出して`IDebugProcess2::EnumPrograms`し、呼び出す[QueryInterface](/cpp/atl/queryinterface)各[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) を取得するインターフェイス[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)インターフェイス)。  
  
-   プロセスの各プログラムをデバッグできます DEs の一覧を生成 (を使用して[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md))。  
  
-   各プログラムの編集と続行 (ENC) の更新プログラムの適用 (IDebugProcess2::EnumPrograms を呼び出すし、呼び出すことによって[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md))。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)