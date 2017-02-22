---
title: "方法: オブジェクト マネージャにライブラリを登録 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ライブラリ、オブジェクト マネージャーに登録します。"
  - "IVsLibrary2 インターフェイス、オブジェクト マネージャーでライブラリの登録"
  - "IVsSimpleLibrary2 インターフェイス、オブジェクト マネージャーでライブラリの登録"
  - "IVsObjectManager2 インターフェイス、オブジェクト マネージャーでライブラリの登録"
  - "ライブラリ、ツールのシンボル参照"
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: オブジェクト マネージャにライブラリを登録
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ツール **クラス ビュー**  など **オブジェクト ブラウザー**  はシンボル参照して  **呼び出しブラウザー**  と  **シンボルの検索結果**  はプロジェクトまたは外部コンポーネントのシンボルを表示することができます。  シンボルは名前空間クラスインターフェイスメソッドおよびそのほかの言語要素が含まれます。  ライブラリはこれらのシンボルを追跡しデータ ツールの設定 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクト マネージャーに公開します。  
  
 オブジェクト マネージャーはすべての使用可能なライブラリを追跡します。  各ライブラリはオブジェクト マネージャーにシンボル参照がシンボルを提供する前に登録する必要があります。  
  
 通常VSPackage の読み込み時にライブラリを登録します。  ただし必要に応じて別の時点にできます。  VSPackage の終了時にライブラリの登録を解除します。  
  
 ライブラリを登録するには<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> のメソッドを使用します。  マネージ コード ライブラリの場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> のメソッドを使用します。  
  
 ライブラリの登録を解除するには<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> のメソッドを使用します。  
  
 オブジェクト マネージャーへの参照を <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> は`GetService` のメソッドに移動するには<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> サービス ID を渡します。  
  
## オブジェクト マネージャーを使用してライブラリを登録または登録解除します  
  
#### オブジェクト マネージャーを使用してライブラリを登録するには  
  
1.  ライブラリを作成します。  
  
    ```vb#  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```c#  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 型のオブジェクトへの参照を取得し<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> のメソッドを呼び出します。  
  
    ```vb#  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```c#  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### オブジェクト マネージャーを使用してライブラリの登録を解除します。  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 型のオブジェクトへの参照を取得し<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> のメソッドを呼び出します。  
  
    ```vb#  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```c#  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## 参照  
 [従来の言語サービスの拡張機能](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [シンボル参照のツールのサポート](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [方法: オブジェクト マネージャーにライブラリによって提供されるシンボルのリストを公開](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)