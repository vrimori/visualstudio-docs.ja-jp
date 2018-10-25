---
title: 特殊化された展開の処理 |Microsoft Docs
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
- deploying applications [Visual Studio SDK]
- specialized deployment
ms.assetid: de068b6a-e806-45f0-9dec-2458fbb486f7
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8568794b46a8d94e8d186fe297e9bb0d1cf53a3c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827461"
---
# <a name="handling-specialized-deployment"></a>特別な展開の処理
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

展開は、プロジェクトの省略可能な操作です。 Web プロジェクトは、たとえば、Web サーバーを更新するプロジェクトへのデプロイをサポートします。 同様に、**スマート デバイス**プロジェクトは、ターゲット デバイスにビルドされたアプリケーションをコピーする展開をサポートしています。 プロジェクト サブタイプが実装することによって特殊化された展開の動作を指定できます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>インターフェイス。 このインターフェイスは、デプロイ操作の完全なセットを定義します。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>  
  
  別のスレッドで実際の展開操作を実行する必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ユーザーの操作により応答性の高い。 によって提供されるメソッド<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>によって非同期的と呼ばれる[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]し、必要に応じていつでもデプロイ操作の状態を照会するか、操作を停止する環境をできるように、バック グラウンドで動作します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>展開コマンドを選択すると、デプロイ操作のインターフェイスは、環境によって呼び出されます。  
  
  呼び出す必要があるプロジェクト サブタイプに環境をデプロイ操作が開始または終了を通知する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnStartDeploy%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnEndDeploy%2A>メソッド。  
  
## <a name="handling-specialized-deployment"></a>特別な展開の処理  
  
#### <a name="to-handle-a-specialized-deployment-by-a-subtype-project"></a>プロジェクト サブタイプによって特殊化された展開を処理するには  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>デプロイの状態イベントの通知を受信するための環境を登録します。  
  
    ```vb  
    Private adviseSink As Microsoft.VisualStudio.Shell.EventSinkCollection = New Microsoft.VisualStudio.Shell.EventSinkCollection()  
    Public Function AdviseDeployStatusCallback(ByVal pIVsDeployStatusCallback As IVsDeployStatusCallback, _  
                                               ByRef pdwCookie As UInteger) As Integer  
  
        If pIVsDeployStatusCallback Is Nothing Then  
            Throw New ArgumentNullException("pIVsDeployStatusCallback")  
        End If  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback)  
        Return VSConstants.S_OK  
  
    End Function  
    ```  
  
    ```csharp  
    private Microsoft.VisualStudio.Shell.EventSinkCollection adviseSink = new Microsoft.VisualStudio.Shell.EventSinkCollection();  
    public int AdviseDeployStatusCallback(IVsDeployStatusCallback pIVsDeployStatusCallback,   
                                          out uint pdwCookie)  
    {  
        if (pIVsDeployStatusCallback == null)  
            throw new ArgumentNullException("pIVsDeployStatusCallback");  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>デプロイの状態イベントの通知を受信する環境の登録をキャンセルするメソッド。  
  
    ```vb  
    Public Function UnadviseDeployStatusCallback(ByVal dwCookie As UInteger) As Integer  
        adviseSink.RemoveAt(dwCookie)  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int UnadviseDeployStatusCallback(uint dwCookie)  
    {  
        adviseSink.RemoveAt(dwCookie);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>アプリケーションに固有のコミット操作を実行するメソッド。  このメソッドは、主にデータベースの配置に使用されます。  
  
    ```vb  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int Commit(uint dwReserved)  
    {  
         //Implement commit operation here.  
         return VSConstants.S_OK;  
    }  
  
    ```  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>ロールバック操作を実行するメソッド。 このメソッドが呼び出されると、展開プロジェクトはな処理を行う変更をロールバックして適切なと、プロジェクトの状態を復元する必要があります。 このメソッドは、主にデータベースの配置に使用されます。  
  
    ```vb  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int Rollback(uint dwReserved)  
    {  
        //Implement Rollback operation here.  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>プロジェクトがデプロイ操作を開始できるかどうかを判断するメソッド。  
  
    ```vb  
    Public Function QueryStartDeploy(ByVal dwOptions As UInteger, ByVal pfSupported As Integer(), ByVal pfReady As Integer()) As Integer  
        If Not pfSupported Is Nothing AndAlso pfSupported.Length > 0 Then  
            pfSupported(0) = 1  
        End If  
        If Not pfReady Is Nothing AndAlso pfReady.Length > 0 Then  
            pfReady(0) = 0  
            If Not deploymentThread Is Nothing AndAlso (Not deploymentThread.IsAlive) Then  
                pfReady(0) = 1  
            End If  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int QueryStartDeploy(uint dwOptions, int[] pfSupported, int[] pfReady)  
    {  
        if (pfSupported != null && pfSupported.Length >0)  
            pfSupported[0] = 1;  
        if (pfReady != null && pfReady.Length >0)  
        {  
            pfReady[0] = 0;  
            if (deploymentThread != null && !deploymentThread.IsAlive)  
                pfReady[0] = 1;  
        }  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>デプロイ操作が正常に完了するかどうかを判断するメソッド。  
  
    ```vb  
    Public Function QueryStatusDeploy(ByRef pfDeployDone As Integer) As Integer  
        pfDeployDone = 1  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            pfDeployDone = 0  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int QueryStatusDeploy(out int pfDeployDone)  
    {  
        pfDeployDone = 1;  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            pfDeployDone = 0;  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>メソッドを個別のスレッドでのデプロイ操作を開始します。 内のアプリケーションの展開に固有のコードを配置、`Deploy`メソッド。  
  
    ```vb  
    Public Function StartDeploy(ByVal pIVsOutputWindowPane As IVsOutputWindowPane, ByVal dwOptions As UInteger) As Integer  
        If pIVsOutputWindowPane Is Nothing Then  
            Throw New ArgumentNullException("pIVsOutputWindowPane")  
        End If  
  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Throw New NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first")  
        End If  
  
        outputWindow = pIVsOutputWindowPane  
  
        ' Notify that deployment is about to begin and see if any user wants to cancel.  
        If (Not NotifyStart()) Then  
            Return VSConstants.E_ABORT  
        End If  
  
        operationCanceled = False  
  
        ' Create and start our thread  
        deploymentThread = New Thread(AddressOf Me.Deploy)  
        deploymentThread.Name = "Deployment Thread"  
        deploymentThread.Start()  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int StartDeploy(IVsOutputWindowPane pIVsOutputWindowPane, uint dwOptions)  
    {  
        if (pIVsOutputWindowPane == null)  
            throw new ArgumentNullException("pIVsOutputWindowPane");  
  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            throw new NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first");  
  
        outputWindow = pIVsOutputWindowPane;  
  
        // Notify that deployment is about to begin and see if any user wants to cancel.  
        if (!NotifyStart())  
            return VSConstants.E_ABORT;  
  
        operationCanceled = false;  
  
        // Create and start our thread  
        deploymentThread = new Thread(new ThreadStart(this.Deploy));  
        deploymentThread.Name = "Deployment Thread";  
        deploymentThread.Start();  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   実装、<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>展開操作を停止するメソッド。 ユーザーが押したときに、このメソッドが呼び出されます、**キャンセル**展開プロセス中にボタンをクリックします。  
  
    ```vb  
    Public Function StopDeploy(ByVal fSync As Integer) As Integer  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Return VSConstants.S_OK  
        End If  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment")  
        operationCanceled = True  
        If fSync <> 0 Then  
            ' Synchronous request, wait for the thread to terminate.  
            If (Not deploymentThread.Join(10000)) Then  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread")  
                deploymentThread.Abort()  
            End If  
        End If  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int StopDeploy(int fSync)  
    {  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            return VSConstants.S_OK;  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment");  
        operationCanceled = true;  
        if (fSync != 0)  
        {  
            // Synchronous request, wait for the thread to terminate.  
            if (!deploymentThread.Join(10000))  
            {  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread");  
                deploymentThread.Abort();  
            }  
        }  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
> [!NOTE]
>  このトピックで提供されたすべてのコード例は、例のパーツ[VSSDK のサンプル](../../misc/vssdk-samples.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)

