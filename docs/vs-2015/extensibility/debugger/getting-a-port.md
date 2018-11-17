---
title: ポートの取得 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 660ead58af40f85b4da4d68d7172866f5fe1fd0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789903"
---
# <a name="getting-a-port"></a>ポートの取得
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ポートは、プロセスが実行されているマシンへの接続を表します。 そのマシンは、ローカル コンピューターまたはリモート コンピューターの可能性があります (これ場合によって実行される可能性が非 Windows ベースのオペレーティング システムは、参照してください[ポート](../../extensibility/debugger/ports.md)詳細については)。  
  
 ポートがによって表される、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイス。 ポートが接続されているコンピューターで実行されているプロセスに関する情報の取得に使用されます。  
  
 デバッグ エンジンには、ポートとプログラムのノードを登録するために、プロセス情報の要求を満たすために、ポートへのアクセスが必要があります。 たとえば、デバッグ エンジンを実装する場合、 [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)インターフェイスの実装、 [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)メソッドは、必要なプロセスのポートを依頼する可能性があります返される情報。  
  
 Visual Studio がデバッグ エンジンに必要なポートを提供し、ポートのサプライヤーからこのポートを取得します。 プログラムにアタッチされている場合 (または例外のため、デバッガー内でいずれかから、スローされた、ジャスト イン タイム [JIT] ダイアログ ボックスをトリガーする)、ユーザーが使用する、選択したトランスポート (ポート サプライヤーに別の名前) を指定します。 それ以外の場合、ユーザーが、デバッガー内からプログラムを起動、プロジェクト システムを使用するポートのサプライヤーを指定します。 いずれの場合は、Visual Studio をによって表されるポート サプライヤーは、インスタンス化します、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイスし、新しいポートを呼び出すことによって要求[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)で、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)インターフェイス。 このポートは 1 つの形式でのデバッグ エンジンまたは別に渡されます。  
  
## <a name="example"></a>例  
 次のコードに指定されたポートを使用する方法を示しています。 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)内のノードでプログラムを登録する[ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)します。 この概念に直接関連しないパラメーターは、わかりやすくするため除外されました。  
  
> [!NOTE]
>  この例は、ポートを使用して起動し、プロセスを再開しを前提としています、 [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)ポートでインターフェイスを実装します。 これは、これらのタスクを実行する唯一の方法ではありませんし、ポート可能性がありますも関与しない以外のプログラムのことができます[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)に指定します。  
  
```cpp#  
// This is an IDebugEngineLaunch2 method.  
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,  
                                      IDebugPort2 *pPort,  
                                      /* omitted parameters */,  
                                      IDebugProcess2**ppDebugProcess)  
{  
    // do stuff here to set up for a launch (such as handling the other parameters)  
    ...  
  
    // Now get the IPortNotify2 interface so we can register a program node  
    // in CDebugEngine::ResumeProcess.  
    CComPtr<IDebugDefaultPort2> spDefaultPort;  
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);  
    if (SUCCEEDED(hr))  
    {  
        CComPtr<IDebugPortNotify2> spPortNotify;  
        hr = spDefaultPort->GetPortNotify(&spPortNotify);  
        if (SUCCEEDED(hr))  
        {  
            // Remember the port notify so we can use it in ResumeProcess.  
            m_spPortNotify = spPortNotify;  
  
            // Now launch the process in a suspended state and return the  
            // IDebugProcess2 interface  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = pPort->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                // pass on the parameters we were given (omitted here)  
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)  
            }  
        }  
    }  
    return(hr);  
}  
  
HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)  
{  
    // Make a program node for this process  
    HRESULT hr;  
    CComPtr<IDebugProgramNode2> spProgramNode;  
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);  
    if (SUCCEEDED(hr))  
    {  
        hr = m_spPortNotify->AddProgramNode(spProgramNode);  
        if (SUCCEEDED(hr))  
        {  
            // resume execution of the process using the port given to us earlier.  
           // (Querying for the IDebugPortEx2 interface is valid here since  
           // that's how we got the IDebugPortNotify2 interface in the first place.)  
            CComPtr<IDebugPortEx2> spPortEx;  
            hr = m_spPortNotify->QueryInterface(&spPortEx);  
            if (SUCCEEDED(hr))  
            {  
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [プログラムの登録](../../extensibility/debugger/registering-the-program.md)   
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [ポート サプライヤー](../../extensibility/debugger/port-suppliers.md)   
 [ポート](../../extensibility/debugger/ports.md)

