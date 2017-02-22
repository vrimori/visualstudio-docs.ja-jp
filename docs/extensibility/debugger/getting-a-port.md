---
title: "ポートを取得します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ポートを取得します。"
  - "[デバッグの SDK] をデバッグするには、ポートします。"
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# ポートを取得します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ポートはプロセスが実行されているコンピューターへの接続を表します。  そのコンピューターでは非ウィンドウ ベースのオペレーティング システムを実行するリモート コンピューターとローカル コンピューター \(できます。; 詳細については[ポート](../../extensibility/debugger/ports.md) を参照してください。  
  
 ポートは [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) のインターフェイスによって表されます。  ポートに接続するコンピューターで実行されているプロセスに関する情報を取得するために使用されます。  
  
 ポートへのデバッグ エンジンのポートにアクセスする必要があるプログラムのノードを登録しプロセス情報の要求を満たすため。  たとえばデバッグ エンジンは [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) のインターフェイスを実装している場合[GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) のメソッドの実装は必要なプロセス情報を返すことができるようにするために呼び出すことができます。  
  
 Visual Studio ではデバッグ エンジンに必要なポートを指定しポートのサプライヤーからこのポートを取得します。  プログラムがデバッガーではJust\-In\-Time \[入力\] JIT ダイアログ ボックスを開始する\) 例外がスローされましたアタッチされている場合はユーザーが使用するポートのコピー \(サプライヤーの別の名前\) の選択されます。  そうしないとユーザーがデバッガーでプログラムを起動しプロジェクト システムが使用するポートの業者を指定します。  いずれの場合も[IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) のインターフェイスで表されるポートのサプライヤーのインスタンスを作成しそのポートを [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) のインターフェイスに [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) を呼び出しています。  このポートは 1 とおりの形式や別のデバッグ エンジンに渡されます。  
  
## 使用例  
 このコードは [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) プログラムのノードを登録するに [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) に指定されたポートを使用する方法を示します。  この概念と直接関連していないパラメーターが明確にするために省略されています。  
  
> [!NOTE]
>  この例ではプロセスを起動して再開するにはポートを使用し[IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) のインターフェイスがポートで実行することを前提とします。  これはこれらのタスクを実行する唯一の方法でなく指定されたプログラムの [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) を持つようにポートでは複雑ではない可能性があります。  
  
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
  
## 参照  
 [プログラムを登録します。](../../extensibility/debugger/registering-the-program.md)   
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [ポートの仕入先](../../extensibility/debugger/port-suppliers.md)   
 [ポート](../../extensibility/debugger/ports.md)