---
title: "IDebugProgramPublisher2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 242221c8cc3ffad51fa21f71d6209208b58ae6e6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
このインターフェイスは、デバッグ エンジン (DE) またはデバッグするためのプログラムを登録するカスタム ポート納入業者を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 Visual Studio では、複数のプロセスでデバッグするために表示されるようにするために、デバッグ中のプログラムを登録するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 COM の呼び出し`CoCreateInstance`で機能`CLSID_ProgramPublisher`(この例を参照してください) このインターフェイスを取得します。 DE やカスタム ポートのサプライヤーは、このインターフェイスを使用して、デバッグ中のプログラムを表すプログラム ノードを登録します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 このインターフェイスでは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|プログラムのノードを使用できるように DEs およびセッション デバッグ マネージャー (SDM)。|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|使用できなくするようにプログラム ノードを削除します。|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|プログラムはにより DEs および、SDM を使用できます。|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|使用可能なが不要になったように、プログラムを削除します。|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|デバッガーが存在することを示すフラグを設定します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスを使用可能プログラムとプログラムのノード (つまり、「パブリッシュ」して) DEs およびセッション デバッグ マネージャー (SDM) で使用します。 公開されたプログラムとプログラムのノードにアクセスするには、使用、 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)インターフェイスです。 これは、Visual Studio は、プログラムをデバッグすることを認識できる唯一の方法です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
 この例では、プログラムの発行元をインスタンス化し、[プログラム] ノードを登録する方法を示します。 これは、チュートリアルから取得[プログラム ノードを公開](http://msdn.microsoft.com/en-us/d0100e02-4e2b-4e72-9e90-f7bc11777bae)です。  
  
```cpp  
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
