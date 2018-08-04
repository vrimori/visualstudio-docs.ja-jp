---
title: '方法: オブジェクト マネージャーにライブラリの登録 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61976fbc63efd4c15e5ed88a159ea8e73bdf38f3
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513323"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>方法: オブジェクト マネージャーにライブラリを登録します。
などのシンボル参照ツール**クラス ビュー**、**オブジェクト ブラウザー**、**呼び出しブラウザー**と**シンボルの検索結果**、表示することを有効にします。シンボル、プロジェクトや外部コンポーネントです。 シンボルには、名前空間、クラス、インターフェイス、メソッド、およびその他の言語要素が含まれます。 ライブラリはこれらのシンボルを追跡し、それらを公開、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]オブジェクト マネージャー、データを使用して、ツールを設定します。  
  
 オブジェクト マネージャーは、使用可能なすべてのライブラリを追跡します。 各ライブラリは、シンボル参照ツールのシンボルを提供する前に、オブジェクト マネージャーを登録する必要があります。  
  
 通常、VSPackage の読み込み時に、ライブラリを登録します。 ただし、その実行できます別の時点で、必要に応じて。 VSPackage がシャット ダウン時に、ライブラリが登録解除します。  
  
 ライブラリを登録するには、使用、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A>メソッド。 マネージ コード ライブラリを使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>メソッド。  
  
 ライブラリの登録を解除するには、使用、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A>メソッド。  
  
 オブジェクト マネージャーへの参照を取得する<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>、渡す、<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager>サービス ID を`GetService`メソッド。  
  
## <a name="register-and-unregister-a-library-with-the-object-manager"></a>登録およびオブジェクト マネージャーにライブラリを登録解除  
  
### <a name="to-register-a-library-with-the-object-manager"></a>オブジェクト マネージャーにライブラリを登録するには  
  
1.  ライブラリを作成します。  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  オブジェクトへの参照を取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>を呼び出すし、入力、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>メソッド。  
  
    ```vb  
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
  
    ```csharp  
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
  
### <a name="to-unregister-a-library-with-the-object-manager"></a>オブジェクト マネージャーで、ライブラリの登録を解除するには  
  
1.  オブジェクトへの参照を取得、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>を呼び出すし、入力、<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A>メソッド。  
  
    ```vb  
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
  
    ```csharp  
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
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービス拡張機能](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [シンボル参照ツールをサポートします。](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [方法: オブジェクト マネージャーにライブラリによって提供されるシンボルのリストを公開](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)