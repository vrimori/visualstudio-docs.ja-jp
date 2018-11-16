---
title: 従来の言語サービスのカスタム ドキュメント プロパティの |Microsoft Docs
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
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9760ba82c7f40a3fc7768e56111352eb384456fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750686"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>従来の言語サービスのカスタム ドキュメント プロパティ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ドキュメントのプロパティを表示できる、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **プロパティ**ウィンドウ。 一般に、プログラミング言語には個々 のソース ファイルに関連付けられているプロパティはありません。 ただし、XML では、エンコード、スキーマ、およびスタイル シートに影響するドキュメント プロパティをサポートしています。  
  
## <a name="discussion"></a>説明  
 お使いの言語では、カスタム ドキュメント プロパティを必要とする場合からクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.DocumentProperties>クラスし、派生クラスで、必要なプロパティを実装します。  
  
 さらに、ドキュメントのプロパティは、通常、ソース ファイル自体に格納します。 言語サービスで表示するソース ファイルのプロパティ情報を解析する必要があります、**プロパティ**ウィンドウ内のドキュメント プロパティに変更が行われたときに、ソース ファイルを更新して、 **プロパティ**ウィンドウ。  
  
## <a name="customizing-the-documentproperties-class"></a>DocumentProperties クラスをカスタマイズします。  
 カスタム ドキュメント プロパティをサポートするからクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.DocumentProperties>クラスし、必要な数だけプロパティを追加します。 整理するためのユーザー属性を指定することも必要があります、**プロパティ** ウィンドウの表示。 プロパティのみを持つ場合、`get`アクセサー、読み取り専用で表示されるように、**プロパティ**ウィンドウ。 プロパティは、両方を持つ場合`get`と`set`アクセサー プロパティも更新するのには、**プロパティ**ウィンドウ。  
  
### <a name="example"></a>例  
 派生したクラスの例を次に示します<xref:Microsoft.VisualStudio.Package.DocumentProperties>、2 つのプロパティ、ファイル名と説明を表示します。 プロパティを更新するときに、カスタム メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラスがソース ファイルにプロパティの書き込み先と呼ばれます。  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="instantiating-the-custom-documentproperties-class"></a>カスタム DocumentProperties クラスをインスタンス化します。  
 オーバーライドする必要があります、カスタム ドキュメント プロパティのクラスをインスタンス化する、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>のバージョンのメソッド、<xref:Microsoft.VisualStudio.Package.LanguageService>の 1 つのインスタンスを返すために、<xref:Microsoft.VisualStudio.Package.DocumentProperties>クラス。  
  
### <a name="example"></a>例  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## <a name="properties-in-the-source-file"></a>ソース ファイル内のプロパティ  
 ドキュメントのプロパティは、通常、ソース ファイルに固有であるために、値は、ソース ファイル自体に格納されます。 これには、言語パーサーまたはこれらのプロパティを定義するスキャナーからのサポートが必要です。 たとえば、XML ドキュメントのプロパティは、ルート ノードに格納されます。 ルート ノードの値が変更されたときに、**プロパティ**ウィンドウの値が変更され、エディターで、ルート ノードが更新されます。  
  
### <a name="example"></a>例  
 この例では、"Filename"と"Description"で、ソース ファイルの最初の 2 つの行として、特殊なコメントのヘッダーに埋め込まれているプロパティを格納します。  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 この例では、取得およびユーザーがソース ファイルを直接変更する場合に、プロパティを更新する方法も、ソース ファイルの最初の 2 つの行からドキュメントのプロパティを設定するために必要な 2 つの方法を示します。 `SetPropertyValue`ここでは、同じ例ではメソッドから呼び出す 1 つ、`TestDocumentProperties`クラス「DocumentProperties クラスのカスタマイズ」セクションで示すようにします。  
  
 この例では、スキャナーを使用して、最初の 2 行のトークンの種類を決定します。 この例では、例示を目的としてのみです。 このような状況をより一般的なアプローチと呼ばれるもの解析ツリー、ツリーの各ノードが、特定のトークンに関する情報を格納する場所にソース ファイルを解析することです。 ルート ノードには、ドキュメントのプロパティが含まれます。  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの特徴](../../extensibility/internals/legacy-language-service-features1.md)

