---
title: レガシ言語 service2 などのパラメーター ヒント |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bee48d3688a43a3dbfb32848818c318f1cf7b2d7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547937"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>従来の言語サービスでのパラメーター ヒント
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[レガシ言語 service2 などのパラメーター ヒント](https://docs.microsoft.com/visualstudio/extensibility/internals/parameter-info-in-a-legacy-language-service2)します。  
  
パラメーターの IntelliSense のヒントは、ユーザーがパラメーター リストを入力すると、メソッドのシグネチャを表示するツールヒントに start メソッドのパラメーター リストの文字 (通常、開きかっこを入力)。 各パラメーターを入力し、パラメーター区切り記号 (コンマ) が型指定された、次のパラメーターを太字で表示するツールヒントが更新されます。  
  
 マネージ パッケージ フレームワーク (MPF) クラスは、パラメーター ヒントを管理するためのサポートを提供します。 パーサーには、パラメーターの開始、パラメーター次に、およびパラメーター最後の文字であり、メソッド シグネチャとその関連付けられているパラメーターの一覧を指定する必要がありますを検出する必要があります。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 詳細については、次を参照してください。[エディターと言語サービス拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="implementation"></a>実装  
 パーサーは、トリガーの値を設定する必要があります<xref:Microsoft.VisualStudio.Package.TokenTriggers>パラメーター リストの開始文字 (多くの場合、始めかっこ) を見つけたときに設定されます。 設定する必要がありますが、<xref:Microsoft.VisualStudio.Package.TokenTriggers>パラメーター区切り記号 (コンマでは多くの場合) を見つけたときにトリガーします。 これにより、パラメーター ヒントを更新し、次のパラメーターを太字で表示されます。 パーサーは、トリガーの値を設定する必要があります<xref:Microsoft.VisualStudio.Package.TokenTriggers>とき場合パラメーター リストの末尾文字 (多くの場合、閉じかっこ) を検索します。  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>トリガー値への呼び出しを開始する、<xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A>メソッドを呼び出して、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッド パーサーの解析の理由で<xref:Microsoft.VisualStudio.Package.ParseReason>します。 メソッド シグネチャに一致させるの一覧を返しますが、パーサーは、前に、パラメーター リストの先頭文字の識別子が認識されているメソッド名である判断した場合、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト。 任意のメソッド シグネチャがわかった場合は、一覧の最初のシグネチャを持つパラメーター ヒントが表示されます。 署名の詳細の入力には、このヒントは更新されます。 パラメーター リストの最後の文字を入力すると、パラメーター ヒントはビューから削除されます。  
  
> [!NOTE]
>  パラメーター ヒント、適切な形式は、プロパティを上書きする必要があります、<xref:Microsoft.VisualStudio.Package.Methods>適切な文字を指定するクラス。 ベース<xref:Microsoft.VisualStudio.Package.Methods>クラスは、c# のメソッド シグネチャのスタイル。 参照してください、<xref:Microsoft.VisualStudio.Package.Methods>この実行方法について詳しくクラス。  
  
## <a name="enabling-support-for-the-parameter-info"></a>パラメーター ヒントのサポートを有効にします。  
 パラメーター ヒントのツールヒントをサポートするために設定する必要があります、`ShowCompletion`名前付きのパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>に`true`します。 言語サービスからこのレジストリ エントリの値を読み取り、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>プロパティ。  
  
 さらに、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>にプロパティを設定する必要があります`true`パラメーター ヒントのツールヒントに表示されるのです。  
  
### <a name="example"></a>例  
 パラメーターの一覧の文字を検出し、適切なトリガーを設定する簡単な例を次に示します。 この例では、例示を目的としてのみです。 スキャナーにメソッドが含まれていると想定して`GetNextToken`を識別し、行のテキストからトークンを返します。 適切な種類の文字が認識されるたびに、コード例は単純に、トリガーを設定します。  
  
```csharp  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>パーサーでパラメーターのヒントをサポートしています。  
 <xref:Microsoft.VisualStudio.Package.Source>クラスは、いくつかの前提条件の内容について、<xref:Microsoft.VisualStudio.Package.AuthoringScope>と<xref:Microsoft.VisualStudio.Package.AuthoringSink>パラメーター ヒントのツールヒントが表示され、更新されたときにします。  
  
-   パーサーが指定された<xref:Microsoft.VisualStudio.Package.ParseReason>パラメーター リストの開始文字が入力されます。  
  
-   指定された場所、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクトがパラメーター リストの先頭文字の直後にします。 パーサーは、配置、バージョンの一覧に保管するで使用可能なすべてのメソッド宣言の署名を収集する必要があります、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト。 この一覧には、メソッド名が含まれています。 メソッド型 (または戻り値の型)、および可能なパラメーターの一覧。 この一覧は、メソッド シグネチャのパラメーター ヒントのツールヒントに表示する署名後で検索されます。  
  
 パーサーによって指定された行を解析する必要があります、<xref:Microsoft.VisualStudio.Package.ParseRequest>入力されているメソッドのほか、ユーザーの名前を収集するためにオブジェクトがパラメーターを入力します。 これは、メソッドの名前を渡すことによって実現されます、<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>メソッドを<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトと、呼び出し、<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>メソッド パラメーター リストの先頭文字が解析を呼び出す、<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>メソッドとパラメーター リスト次の文字が最後に呼び出すと、解析された、<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>メソッド パラメーター リストの最後の文字の解析時にします。 これらのメソッド呼び出しの結果を使用して、<xref:Microsoft.VisualStudio.Package.Source>パラメーター ヒントを適切に更新するクラス。  
  
### <a name="example"></a>例  
 ここでは、ユーザーが入力テキストの行です。 線の下の数値は、(解析移動左から右へと仮定) の行では、その位置にあるパーサーによってどの手順が実行されるを示しています。 前提をここでは、ある行の前にすべてのものが既に解析されて"testfunc"メソッドのシグネチャのメソッド シグネチャのです。  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 以下は、パーサーが取る手順の概要します。  
  
1.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>テキスト"testfunc"を使用します。  
  
2.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>します。  
  
3.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>します。  
  
4.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>します。

