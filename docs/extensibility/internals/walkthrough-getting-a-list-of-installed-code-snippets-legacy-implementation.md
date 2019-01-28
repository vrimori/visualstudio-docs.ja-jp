---
title: コード スニペット (レガシ) がインストールされている一覧の取得 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, retrieving list
- code snippets, retrieving list
- GetSnippets method
ms.assetid: 7d142f8b-35b1-44c4-a13e-f89f6460c906
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e1708f7d2bf77325eced88f1f835e62073c3d18
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975427"
---
# <a name="walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation"></a>チュートリアル: インストールされているコード スニペット (従来の実装) の一覧を取得します。
コード スニペットは、(これにより、インストールされているコード スニペットの一覧の中から選択) メニューのコマンドを使用して、または、元のバッファーに挿入できるコードの IntelliSense のコンプリート リストから、スニペット ショートカットを選択します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.EnumerateExpansions%2A>メソッドは、言語固有の GUID のすべてのコード スニペットを取得します。 これらのスニペットのショートカットは、IntelliSense のコンプリート リストに挿入できます。  
  
 参照してください[従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)詳細については、マネージ パッケージ フレームワーク (MPF) の言語サービスでコード スニペットを実装します。  
  
### <a name="to-retrieve-a-list-of-code-snippets"></a>コード スニペットの一覧を取得するには  
  
1.  次のコードでは、特定の言語コード スニペットの一覧を取得する方法を示します。 配列で、結果が格納されている<xref:Microsoft.VisualStudio.TextManager.Interop.VsExpansion>構造体。 このメソッドは、静的な<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>を取得するメソッド、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>からインターフェイス、<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>サービス。 ただし、サービス プロバイダーが、VSPackage と呼び出しに指定された使用も、<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>メソッド。  
  
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
  
1.  次のメソッドを呼び出す方法を示しています、`GetSnippets`解析操作の完了時のメソッド。 <xref:Microsoft.VisualStudio.Package.LanguageService.OnParseComplete%2A>解析操作の理由で開始された後、メソッドが呼び出された<xref:Microsoft.VisualStudio.Package.ParseReason>します。  
  
> [!NOTE]
>  `expansionsList`配列リストでは、パフォーマンス上の理由がキャッシュされます。 一覧には、言語サービスを停止して再度読み込むまで、スニペットへの変更は反映されません (停止して再起動をなど[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)])。  
  
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
  
1.  次のコードは、によって返されるスニペットの情報を使用する方法を示します、`GetSnippets`メソッド。 `AddSnippets`コード スニペットの一覧を設定するために使用するすべての解析理由に応じて、パーサーからメソッドが呼び出されます。 最初に、完全な解析が完了した後、配置がかかります。  
  
     `AddDeclaration`メソッドは、後で、入力候補一覧に表示される宣言のリストを構築します。  
  
     `TestDeclaration`クラスには宣言の型と同様に、入力候補一覧に表示できるすべての情報が含まれています。  
  
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
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスでのコード スニペットのサポート](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)