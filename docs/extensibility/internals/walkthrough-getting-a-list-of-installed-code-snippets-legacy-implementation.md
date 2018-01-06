---
title: "コード スニペット (レガシ) がインストールされている一覧の取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 53d0a4fc5abc43bc446b3523cc7e8075eb7d4aa9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>チュートリアル: インストールされているコード スニペット (レガシ実装) の一覧を取得します。
コード スニペットはまたはのいずれか (これにより、インストールされているコード スニペットの一覧を選択) メニューのコマンドでは、ソース バッファーに挿入できるコードの IntelliSense コンプリート リストから、スニペット ショートカットを選択します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>メソッドは、特定の言語の GUID のすべてのコード スニペットを取得します。 そのスニペット ショートカットは、IntelliSense コンプリート リストに挿入できます。  
  
 参照してください[レガシ言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)詳細については、マネージ パッケージ フレームワーク (MPF) 言語サービスでのコード スニペットを実装する方法です。  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>コード スニペットの一覧を取得するには  
  
1.  次のコードは、特定の言語のコード スニペットの一覧を取得する方法を示しています。 配列の結果が格納されている<xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>構造体。 このメソッドは、静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>取得するメソッド、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>サービス。 ただし、VSPackage と呼び出しに指定されたサービス プロバイダーは、使用も、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>メソッドです。  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Package;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.TextManager.Interop;  
  
    [Guid("00000000-0000-0000-0000-000000000000")] //create a new GUID for the language service  
    namespace TestLanguage  
    {  
        class TestLanguageService : LanguageService  
        {  
            private void GetSnippets(Guid languageGuid,  
                                     ref ArrayList expansionsList)  
            {  
                IVsTextManager textManager = (IVsTextManager)Package.GetGlobalService(typeof(SVsTextManager));  
                if (textManager != null)  
                {  
                    IVsTextManager2 textManager2 = (IVsTextManager2)textManager;  
                    if (textManager2 != null)  
                    {  
                        IVsExpansionManager expansionManager = null;  
                        textManager2.GetExpansionManager(out expansionManager);  
                        if (expansionManager != null)  
                        {  
                            // Tell the environment to fetch all of our snippets.  
                            IVsExpansionEnumeration expansionEnumerator = null;  
                            expansionManager.EnumerateExpansions(languageGuid,  
                            0,     // return all info  
                            null,    // return all types  
                            0,     // return all types  
                            1,     // include snippets without types  
                            0,     // do not include duplicates  
                            out expansionEnumerator);  
                            if (expansionEnumerator != null)  
                            {  
                                // Cache our expansions in a VsExpansion array   
                                uint count   = 0;  
                                uint fetched = 0;  
                                VsExpansion expansionInfo = new VsExpansion();  
                                IntPtr[] pExpansionInfo   = new IntPtr[1];  
  
                                // Allocate enough memory for one VSExpansion structure. This memory is filled in by the Next method.  
                                pExpansionInfo[0] = Marshal.AllocCoTaskMem(Marshal.SizeOf(expansionInfo));  
  
                                expansionEnumerator.GetCount(out count);  
                                for (uint i = 0; i < count; i++)  
                                {  
                                    expansionEnumerator.Next(1, pExpansionInfo, out fetched);  
                                    if (fetched > 0)  
                                    {  
                                        // Convert the returned blob of data into a structure that can be read in managed code.  
                                        expansionInfo = (VsExpansion)Marshal.PtrToStructure(pExpansionInfo[0], typeof(VsExpansion));  
  
                                        if (!String.IsNullOrEmpty(expansionInfo.shortcut))  
                                        {  
                                            expansionsList.Add(expansionInfo);  
                                        }  
                                    }  
                                }  
                                Marshal.FreeCoTaskMem(pExpansionInfo[0]);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
### <a name="to-call-the-getsnippets-method"></a>GetSnippets メソッドを呼び出す  
  
1.  次のメソッドを呼び出す方法を示しています、`GetSnippets`解析操作の完了時のメソッドです。 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>解析操作の理由で開始された後にメソッドが呼び出された<xref:Microsoft.VisualStudio.Package.ParseReason>です。  
  
> [!NOTE]
>  `expansionsList`パフォーマンス上の理由に対してキャッシュ リストの配列。 一覧には、言語サービスが停止され、再読み込みされるまで、スニペットへの変更は反映されません (たとえば、停止して再開[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)])。  
  
```csharp  
class TestLanguageService : LanguageService  
{  
    private ArrayList expansionsList;  
  
    public override void OnParseComplete(ParseRequest req)  
    {  
        if (this.expansionsList == null)  
        {  
            this.expansionsList = new ArrayList();  
            GetSnippets(this.GetLanguageServiceGuid(),  
                ref this.expansionsList);  
        }  
    }  
}  
```  
  
### <a name="to-use-the-snippet-information"></a>スニペットの情報を使用するには  
  
1.  次のコードによって返されるスニペット情報を使用する方法を示しています、`GetSnippets`メソッドです。 `AddSnippets`メソッドはどのような解析理由コード スニペットの一覧を設定するために使用する応答のパーサーから呼び出されます。 これは、後に実行が最初に完全な解析が行われています。  
  
     `AddDeclaration`メソッドは、後で、コンプリート リストに表示される宣言のリストを構築します。  
  
     `TestDeclaration`クラスには、宣言の型と同様に、コンプリート リストで表示できるすべての情報が含まれています。  
  
    ```csharp  
    class TestAuthoringScope : AuthoringScope  
    {  
        public void AddDeclarations(TestDeclaration declaration)  
        {  
            if (m_declarations == null)  
                m_declarations = new List<TestDeclaration>();  
            m_declarations.Add(declaration);  
         }  
    }  
    class TestDeclaration   
    {  
        private string m_name;  
        private string m_description;  
        private string m_type;  
  
        public TestDeclaration(string name, string desc, string type)  
        {  
            m_name = name;  
            m_description = desc;  
            m_type = type;  
        }  
  
    class TestLanguageService : LanguageService  
    {  
        internal void AddSnippets(ref TestAuthoringScope scope)  
        {  
            if (this.expansionsList != null && this.expansionsList.Count > 0)  
            {  
                int count = this.expansionsList.Count;  
                for (int i = 0; i < count; i++)  
                {  
                    VsExpansion expansionInfo = (VsExpansion)this.expansionsList[i];  
                    scope.AddDeclaration(new TestDeclaration(expansionInfo.title,  
                         expansionInfo.description,  
                         "snippet"));  
                }  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>参照  
 [従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)