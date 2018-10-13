---
title: プログラムの登録 |Microsoft Docs
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
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29cc63b2cdc9e965ad52276390d203f41eec4553
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306463"
---
# <a name="registering-the-program"></a>プログラムの登録
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

によって表されるデバッグ エンジンでは、ポート、取得された後、 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)インターフェイス、デバッグするプログラムを有効にするのには、次の手順は、ポートを使用して登録します。 登録されると、プログラムがでは、次のいずれかのデバッグに使用します。  
  
-   使用する実行中のアプリケーションの制御をデバッグするデバッガーのアタッチ、プロセス。  
  
-   -Just-in-time (JIT) デバッグは、ファクトの後は、デバッガーとは無関係に実行されるプログラムのデバッグできます。 実行時のアーキテクチャでは、エラーをキャッチ、したときに、オペレーティング システムの前に、デバッガーに通知またはランタイム環境は、メモリと、エラーが発生したプログラムのリソースを解放します。  
  
## <a name="registering-procedure"></a>プロシージャの登録  
  
#### <a name="to-register-your-program"></a>プログラムを登録するには  
  
1.  呼び出す、 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)ポートによって実装されるメソッド。  
  
     `IDebugPortNotify2::AddProgramNode` ポインターが必要です、 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)インターフェイス。  
  
     通常、オペレーティング システムまたはランタイム環境が読み込まれるプログラムは、プログラムのノードを作成します。 デバッグ エンジン (DE) は、プログラムを読み込むように求められます、DE は作成し、プログラムのノードを登録します。  
  
     次の例では、プログラムを起動し、ポートに登録するデバッグ エンジンを示します。  
  
    > [!NOTE]
    >  これは起動し、プロセスを再開する唯一の方法ではありません。これは、ポートをプログラムに登録の例では主に。  
  
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
  
## <a name="see-also"></a>関連項目  
 [ポートの取得](../../extensibility/debugger/getting-a-port.md)   
 [デバッグするプログラムの有効化](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

