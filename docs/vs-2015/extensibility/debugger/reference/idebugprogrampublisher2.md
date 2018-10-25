---
title: IDebugProgramPublisher2 |Microsoft Docs
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
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6da3a4404c9d982081ce21c5b1e253f6992042b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216316"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、デバッグ エンジン (DE) またはカスタム ポート サプライヤーがデバッグ用のプログラムを登録できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、複数のプロセス間でのデバッグに表示されるようにするにはデバッグ中のプログラムを登録するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 COM の呼び出し`CoCreateInstance`関数と`CLSID_ProgramPublisher`(例を参照してください) このインターフェイスを取得します。 DE、またはカスタムのポート サプライヤーは、デバッグ中のプログラムを表すプログラム ノードを登録するのにこのインターフェイスを使用します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 このインターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|プログラム ノード使用できるように DEs およびセッション デバッグ マネージャー (SDM)。|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|使用できなくするようにプログラム ノードを削除します。|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|プログラムを DEs および、SDM を使用できるようにします。|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|使用できなくするために、プログラムを削除します。|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|デバッガーが存在することを示すフラグを設定します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスを使用可能プログラムとプログラムのノード (つまり、「公開」) DEs およびセッション デバッグ マネージャー (SDM) で使用します。 公開されたプログラムとプログラムのノードにアクセスするには、使用、 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)インターフェイス。 これは、Visual Studio は、プログラムをデバッグすることを認識できる唯一の方法です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
 この例では、プログラムの発行元をインスタンス化し、[プログラム] ノードを登録する方法を示します。 これは、チュートリアルから取得[公開プログラム ノード](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae)します。  
  
```cpp#  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

