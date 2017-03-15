---
title: "従来の言語サービスでカスタム ドキュメント プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "カスタム ドキュメント プロパティ、言語サービス [マネージ パッケージ framework]"
  - "カスタム ドキュメント プロパティ"
  - "言語サービス [マネージ パッケージ フレームワーク] カスタム ドキュメント プロパティ"
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 従来の言語サービスでカスタム ドキュメント プロパティ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ドキュメントは ENT0ENT \[プロパティ\] ウィンドウの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に表示できます。  プログラミング言語の一般に個別のソース ファイルに関連付けられているプロパティはありません。  ただしXML エンコーディングはスキーマやスタイル シートに影響するドキュメント プロパティをサポートします。  
  
## 説明  
 言語がカスタム ドキュメント プロパティが必要な場合は<xref:Microsoft.VisualStudio.Package.DocumentProperties> のクラスからクラスを派生し派生クラスで必要なプロパティを実装する必要があります。  
  
 またドキュメント プロパティはソース ファイル自体で一般的に保存されます。  これは\[出力\] ウィンドウ ENT4ENT のドキュメント プロパティを変更すると ENT3ENT \[出力\] ウィンドウに表示されソース ファイルを更新する言語サービスのソース ファイルからプロパティ情報を解析する必要があります。  
  
## DocumentProperties クラスのカスタマイズ  
 必要なカスタム ドキュメント プロパティをサポートするには<xref:Microsoft.VisualStudio.Package.DocumentProperties> のクラスからクラスを派生しすべてのプロパティを追加します。  また\[出力\] ウィンドウ ENT1ENT な整理するユーザーに属性を指定する必要があります。  プロパティに `get` のアクセサーだけが表示されている場合は\[出力\] ウィンドウで ENT5ENT 読み取り専用として表示されます。  プロパティに `get` と `set` のアクセサーの両方がの場合プロパティは\[ENT9ENT\] ウィンドウで更新できます。  
  
### 例  
 2 種類のプロパティファイル名および説明を表示 <xref:Microsoft.VisualStudio.Package.DocumentProperties> クラスから派生する例を次に示します。  プロパティが更新されるとソース ファイルにプロパティを記述する場合は<xref:Microsoft.VisualStudio.Package.LanguageService> クラスのカスタム メソッドが呼び出されます。  
  
```c#  
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
  
## DocumentProperties のカスタム クラスをインスタンス化できます。  
 カスタム ドキュメント プロパティ クラスのインスタンスを作成するには<xref:Microsoft.VisualStudio.Package.DocumentProperties> クラスのインスタンスを返すように <xref:Microsoft.VisualStudio.Package.LanguageService> クラスのバージョンの <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> のメソッドをオーバーライドする必要があります。  
  
### 例  
  
```c#  
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
  
## ソース ファイルのプロパティ  
 ドキュメント プロパティは通常ソース ファイル固有であるため値はソース ファイル自体に格納されます。  これは言語パーサーまたはスキャナーのサポートがこれらのプロパティを定義する必要があります。  たとえばXML ドキュメントのプロパティはルート ノードに格納されます。  ルート ノードの値には\[出力\] ウィンドウ ENT2ENT な値が変更されたルート ノードがエディターで更新された場合変更されます。  
  
### 例  
 この例では特殊なコメントのヘッダーに埋め込まれたソース ファイルの最初の 2 行のプロパティ 「ファイル名」および 「」を次のように保存されます :  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 この例ではユーザーがソース ファイルを直接変更するとプロパティの更新方法をソース ファイルの最初の 2 行からドキュメント プロパティを取得および設定するために必要な 2 とおりの方法も示します。  次に示す例の `SetPropertyValue` のメソッドは 「セクションで説明した DocumentProperties のクラス」カスタマイズする `TestDocumentProperties` のクラスから呼び出されるものと同じです。  
  
 この例では最初の 2 行のトークンの種類を判断するためにスキャナーを使用します。  この例では説明を目的としています。  この状況では通常はツリーの各ノードは特定のトークンに関する情報が含まれている場合に解析できます。パース ツリーと呼ばれるものにソース ファイルをです。  ルート ノードはドキュメント プロパティが含まれています。  
  
```c#  
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
  
## 参照  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)