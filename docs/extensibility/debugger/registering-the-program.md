---
title: "プログラムを登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プログラムの登録"
  - "[デバッグの SDK] をデバッグするには、プログラムの登録"
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# プログラムを登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンは [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) のインターフェイスで表されるポートを有効にするには次の手順で取得した後でデバッグするプログラムはポートに登録します。  登録されて次のことを 1 でデバッグに使用されています :  
  
-   デバッガーが実行中のアプリケーションの完全なデバッグを制御できるアタッチするプロセス。  
  
-   \(JIT\) デバッガーとは関係なくプログラムの後に実行することのデバッグを割り当てる Just\-In\-Time \(JIT\) デバッグ \(JIT\) できます。  実行時アーキテクチャの違反を検索する場合デバッガーはオペレーティング システムの前に通知されますがランタイム環境ではエラーがプログラムのメモリおよびリソースを解放します。  
  
## プロシージャの登録  
  
#### プログラムを登録するには  
  
1.  メソッドを [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) のポートで実行されて呼び出されます。  
  
     `IDebugPortNotify2::AddProgramNode` は [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) インターフェイスへのポインターを必要とします。  
  
     通常オペレーティング システムまたはランタイム環境がプログラムを読み込むとプログラムのノードを作成します。  デバッグ エンジンは\(DE\) プログラムを読み込むように呼び出された DE はプログラムのノードを作成および登録します。  
  
     次の例はプログラムを起動しポートに登録するデバッグ エンジンを示します。  
  
    > [!NOTE]
    >  これはプロセスを起動して再開する唯一の方法ではありません ; これはポートでプログラムを登録する主な例です。  
  
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
 [ポートを取得します。](../../extensibility/debugger/getting-a-port.md)   
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)