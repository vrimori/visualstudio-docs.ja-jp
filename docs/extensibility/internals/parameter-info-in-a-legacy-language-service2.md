---
title: "レガシ言語 Service2 でパラメーター情報 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense、パラメーター ヒントのツールヒント"
  - "言語サービス [マネージ パッケージ フレームワーク] IntelliSense パラメーター ヒント"
  - "言語サービス [マネージ パッケージ フレームワーク] でサポートするパラメーター ヒント (IntelliSense)"
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 従来の言語サービスでパラメーター情報
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense のパラメーター情報は、ユーザーがパラメーター リストを入力すると、メソッドのシグネチャを表示するツールヒントに start メソッドのパラメーター リストの文字 \(通常、開きかっこを入力\)。 各パラメーターが入力され、パラメーター区切り記号 \(コンマ\) が型指定された、次のパラメーターを太字で表示するツールヒントが更新されます。  
  
 パッケージの管理対象のフレームワーク \(MPF\) クラスでは、パラメーター ヒントを管理するためのサポートを提供します。 パーサーは、パラメーターを開始するパラメーター次に、およびパラメーター最後の文字であり、メソッドのシグネチャと関連付けられているパラメーターの一覧を指定する必要がありますを検出する必要があります。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。 [エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## 実装  
 パーサーは、トリガー値を設定する必要があります <xref:Microsoft.VisualStudio.Package.TokenTriggers> パラメーター リストの先頭文字 \(多くの場合、かっこ\) が検出されるたびに設定します。 設定する必要があります、 <xref:Microsoft.VisualStudio.Package.TokenTriggers> パラメーター区切り記号 \(コンマでは多くの場合\) を検索するときにトリガーします。 これにより、パラメーター ヒント ツールヒントが更新され、次のパラメーターを太字で表示されます。 パーサーは、トリガー値を設定する必要があります <xref:Microsoft.VisualStudio.Package.TokenTriggers> とき場合パラメーター リストの終了文字 \(多くの場合、かっこ\) を検索します。  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> トリガー値への呼び出しを開始する、 <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> メソッドを呼び出して、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 解析理由が付いているメソッドのパーサー <xref:Microsoft.VisualStudio.Package.ParseReason>します。 メソッド署名を照合の一覧を返しますパーサー、認識された場合、パラメーター リストの文字を開始する前に識別子が認識されているメソッドの名前になる、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> オブジェクトです。 任意のメソッドのシグネチャが見つかった場合は、一覧で最初のシグネチャを持つパラメーター ヒントのツールヒントが表示されます。 署名の詳細の入力に、このツール ヒントが更新されます。 パラメーター リストの最後の文字を入力すると、パラメーター ヒントのツールヒントがビューから削除します。  
  
> [!NOTE]
>  パラメーター ヒントのツールヒントが正しく書式設定は、上のプロパティをオーバーライドする必要があります、 <xref:Microsoft.VisualStudio.Package.Methods> 適切な文字を指定するクラス。 基本 <xref:Microsoft.VisualStudio.Package.Methods> クラスには、c\# と想定しています\-スタイル メソッド シグネチャ。 参照してください、 <xref:Microsoft.VisualStudio.Package.Methods> これ行う手順の詳細についてはクラスです。  
  
## パラメーター ヒントのサポートを有効にします。  
 パラメーター ヒントのツールヒントをサポートするために設定する必要があります、 `ShowCompletion` 名前付きのパラメーター、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> に `true`します。 言語サービスはからには、このレジストリ エントリの値を読み取り、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> プロパティです。  
  
 さらに、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> にプロパティを設定する必要があります `true` パラメーター ヒントのツールヒントに表示されるのです。  
  
### 例  
 パラメーターの一覧の文字を検出し、適切なトリガーを設定する簡単な例を次に示します。 この例では、説明の目的でのみです。 スキャナーにメソッドが含まれていると想定して `GetNextToken` を識別し、テキストの行からトークンを返します。 コード例は、適切な文字がときだけで、トリガーを設定します。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## パーサーでパラメーターのヒントをサポートします。  
 <xref:Microsoft.VisualStudio.Package.Source> クラスは、ある程度の推測の内容について、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> と <xref:Microsoft.VisualStudio.Package.AuthoringSink> クラス パラメーター ヒントのツールヒントが表示され、更新されたときにします。  
  
-   パーサーが指定された <xref:Microsoft.VisualStudio.Package.ParseReason> パラメーター リストの先頭文字は型指定されています。  
  
-   指定されている位置、 <xref:Microsoft.VisualStudio.Package.ParseRequest> パラメーター リストは、文字を開始した後すぐにオブジェクトをします。 パーサーは、配置し、バージョンの一覧に格納するで利用可能なすべてのメソッド宣言の署名を収集する必要があります、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> オブジェクトです。 この一覧には、メソッド名が含まれています。 メソッドの種類 \(または戻り値の型\)、および利用可能なパラメーターの一覧です。 この一覧がメソッドの署名または署名のパラメーター ヒントのツールヒントに表示を後で検索されます。  
  
 パーサーで指定された行を解析する必要があります、 <xref:Microsoft.VisualStudio.Package.ParseRequest> ユーザーに沿った距離だけでなく、入力されているメソッドの名前を収集するためにオブジェクトがパラメーターを入力します。 メソッドの名前を渡すことによってこれを行う、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> メソッドを <xref:Microsoft.VisualStudio.Package.AuthoringSink> オブジェクトを呼び出すこと、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> メソッドはパラメーター リストの開始文字とを解析すると、呼び出し、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> メソッドのパラメーター リストの次の文字が解析される際、最後に呼び出すこと、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> メソッドのパラメーター リストの最後の文字が解析されるときです。 これらのメソッド呼び出しの結果を使用して、 <xref:Microsoft.VisualStudio.Package.Source> パラメーター ヒントのツールヒントを適切に更新するクラス。  
  
### 例  
 ユーザーが入力テキストの行を次に示します。 行の下の数字は、\(解析移動左から右へと仮定\) の行の位置にあるパーサーによってどの手順が実行を示します。 前提をここでは、ある行の前にすべてが既に解析されている"testfunc"メソッドのシグネチャを含め、メソッド シグネチャです。  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 パーサーは、手順を次に説明します。  
  
1.  パーサー呼び出し <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> テキスト"testfunc"を使用します。  
  
2.  パーサー呼び出し <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>します。  
  
3.  パーサー呼び出し <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>します。  
  
4.  パーサー呼び出し <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>します。