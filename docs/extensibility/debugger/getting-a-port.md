---
title: "ポートの取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0645cefb4d102f976663bb4293454e2ae6318ad6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="getting-a-port"></a>ポートの取得
ポートは、プロセスを実行しているコンピューターへの接続を表します。 ローカル コンピューターまたはリモート コンピューターにそのマシンがある可能性があります (する可能性のある実行される可能性が非 Windows ベースのオペレーティング システムは、参照してください[ポート](../../extensibility/debugger/ports.md)詳細については)。  
  
 ポートがによって表される、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイスです。 ポートが接続されているコンピューターで実行されているプロセスに関する情報の取得に使用されます。  
  
 デバッグ エンジンには、ポートとプログラムのノードを登録するために、プロセス情報の要求を満たすために、ポートへのアクセスが必要があります。 たとえば、デバッグ エンジンを実装する場合、 [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md)インターフェイスの実装、 [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)メソッドは、必要なプロセスのポートを依頼する可能性があります返される情報です。  
  
 Visual Studio がデバッグ エンジンに必要なポートを提供し、ポートのサプライヤーからこのポートを取得します。 プログラムにアタッチされている場合 (または例外のため、デバッガー内でいずれかからスローされた、ジャスト イン タイム [JIT] ダイアログ ボックスをトリガーする)、ユーザーが使用する、選択したトランスポート (ポート サプライヤーに別の名前) を付与します。 それ以外の場合、ユーザーが、デバッガー内からプログラムを起動、プロジェクト システムを使用するポート仕入先を指定します。 いずれの場合は、Visual Studio はによって表されるポートの仕入先のインスタンスを作成、 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)インターフェイス、および新しいポートを呼び出すことによって要求[AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)で、 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)インターフェイスです。 このポートは、1 つのフォームのデバッグ エンジンは、または別、渡されます。  
  
## <a name="example"></a>例  
 次のコード片に指定されたポートを使用する方法を示しています。 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)プログラムのノードを登録する[ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)です。 この概念に直接関連しないパラメーターは、わかりやすくするため除外されました。  
  
> [!NOTE]
>  この例を起動し、プロセスを再開するポートを使用しているものと想定、 [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)ポートでインターフェイスを実装します。 これは、これらのタスクを実行する唯一の方法ではないと、ポート可能性がありますも関与しない以外の場合、プログラムのことは[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)に指定します。  
  
```cpp  
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
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
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
 [プログラムを登録します。](../../extensibility/debugger/registering-the-program.md)   
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [ポートの仕入先](../../extensibility/debugger/port-suppliers.md)   
 [ポート](../../extensibility/debugger/ports.md)