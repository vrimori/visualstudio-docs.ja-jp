---
title: IEnumDebugPrograms2 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbb01738876eb342fecb83f7f6d09c850ee89636
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247638"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
-   設定、**プロセスにアタッチ**一覧 (呼び出して`IDebugProcess2::EnumPrograms`し、呼び出す[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)各[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) を取得するインターフェイス[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)インターフェイス)。  
  
-   プロセスの各プログラムをデバッグできます DEs の一覧を生成 (を使用して[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md))。  
  
-   各プログラムの編集と続行 (ENC) の更新プログラムの適用 (IDebugProcess2::EnumPrograms を呼び出すし、呼び出すことによって[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md))。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

