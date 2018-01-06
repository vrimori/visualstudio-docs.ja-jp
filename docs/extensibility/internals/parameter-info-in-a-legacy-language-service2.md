---
title: "レガシ言語 Service2 のパラメーター ヒント |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69c65fa2691f71b3bb7f115b771a0de83d543f03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>従来の言語サービスでのパラメーター ヒント
IntelliSense パラメーター情報は、ユーザーがパラメーター リストを入力すると、メソッドのシグネチャを表示するツールヒントが start メソッド パラメーター リストの文字 (通常、開きかっこを入力)。 各パラメーターを入力し、パラメーター区切り記号 (コンマ) が型指定された、次のパラメーターを太字で表示するツールヒントが更新されます。  
  
 マネージ パッケージ フレームワーク (MPF) クラスは、パラメーター ヒントを管理するためのサポートを提供します。 パーサーは、パラメーター開始パラメーター次に、およびパラメーター最後の文字であり、メソッドのシグネチャと、関連付けられているパラメーターの一覧を指定する必要がありますを検出する必要があります。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="implementation"></a>実装  
 パーサーがトリガー値を設定する必要があります<xref:Microsoft.VisualStudio.Package.TokenTriggers>パラメーター リストの開始文字 (多くの場合、始めかっこ) が検出した場合に設定します。 設定する必要があります、<xref:Microsoft.VisualStudio.Package.TokenTriggers>パラメーター区切り記号 (多くの場合はコンマ) が見つかったときにトリガーします。 これにより、パラメーター ヒントを更新し、次のパラメーターを太字で表示されます。 パーサーがトリガー値を設定する必要があります<xref:Microsoft.VisualStudio.Package.TokenTriggers>とき場合パラメーター リストの末尾文字 (多くの場合、閉じかっこ) を検索します。  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers>トリガー値への呼び出しを開始する、<xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A>メソッドを呼び出して、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッド パーサーの解析の理由で<xref:Microsoft.VisualStudio.Package.ParseReason>です。 メソッド シグネチャの一致の一覧を返します、パーサー、認識された場合、パラメーター リストの文字を開始する前に識別子が認識されているメソッド名である、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト。 任意のメソッドのシグネチャが見つかった場合は、リスト内の最初の署名とパラメーター情報ツールヒントが表示されます。 署名の詳細の入力にこのツールヒントが更新されます。 パラメーター リストの最後の文字を入力すると、パラメーター ヒントはビューから削除されます。  
  
> [!NOTE]
>  パラメーター ヒントのツールヒントが正しくフォーマットされているようにのプロパティをオーバーライドする必要があります、<xref:Microsoft.VisualStudio.Package.Methods>適切な文字を指定するクラス。 基本<xref:Microsoft.VisualStudio.Package.Methods>クラスには、c# 前提としています-スタイル メソッド シグネチャ。 参照してください、<xref:Microsoft.VisualStudio.Package.Methods>この実行方法の詳細のクラスです。  
  
## <a name="enabling-support-for-the-parameter-info"></a>パラメーター ヒントのサポートを有効にします。  
 パラメーター ヒントのツールヒントをサポートするために設定する必要があります、`ShowCompletion`名前付きのパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>に`true`です。 言語サービスは、このレジストリ エントリからの値を読み取る、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>プロパティです。  
  
 さらに、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A>プロパティに設定する必要があります`true`パラメーター ヒントのツールヒントに表示されるのです。  
  
### <a name="example"></a>例  
 パラメーターの一覧の文字を検出し、適切なトリガーを設定する簡単な例を次に示します。 この例では、わかりやすくするためだけです。 スキャナーにメソッドが含まれていると想定`GetNextToken`を識別し、テキストの行からトークンを返します。 コード例は、正しい種類の文字を認識するたびに単に、トリガーを設定します。  
  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>パーサーでパラメーターのヒントをサポートします。  
 <xref:Microsoft.VisualStudio.Package.Source>クラスは、いくつかの前提条件の内容について、<xref:Microsoft.VisualStudio.Package.AuthoringScope>と<xref:Microsoft.VisualStudio.Package.AuthoringSink>パラメーター ヒントのツールヒントが表示され、更新されたときのクラスです。  
  
-   パーサーが指定された<xref:Microsoft.VisualStudio.Package.ParseReason>パラメーター リストの先頭文字が入力されます。  
  
-   指定された場所、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクトがパラメーター リストの先頭文字の直後にします。 パーサーが配置およびバージョンの一覧に保存することで利用可能なすべてのメソッド宣言の署名を収集する必要があります、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクト。 この一覧には、メソッド名が含まれています。 メソッドの型 (または戻り値の型)、および利用可能なパラメーターの一覧です。 このリストは、パラメーター ヒントのツールヒントに表示する署名またはメソッドのシグネチャの後で検索されます。  
  
 パーサーによって指定された行を解析する必要があります、<xref:Microsoft.VisualStudio.Package.ParseRequest>名前を入力しているメソッドのほか、ユーザーに沿った距離を収集するオブジェクトがパラメーターを入力します。 メソッドの名前を渡すことによってこれを行う、<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>メソッドを<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクトと呼び出すことで、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 、呼び出すメソッドは、パラメーター リストの先頭文字とは解析、<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>メソッドとパラメーター リスト次の文字が最後に呼び出すと、解析、<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>メソッド パラメーター リストの最後の文字が解析されるときにします。 これらのメソッド呼び出しの結果を使用して、<xref:Microsoft.VisualStudio.Package.Source>パラメーター ヒントを適切に更新するクラス。  
  
### <a name="example"></a>例  
 ここでは、ユーザーが入力テキストの行です。 行の下の番号は、(解析移動左から右へと仮定した場合)、行の位置にあるパーサーによってどの手順が実行されるを示しています。 前提をここでは、ある行の前にすべてのものが既に解析されて"testfunc"メソッドのシグネチャを含め、メソッド シグネチャのです。  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 パーサーは、手順を次に説明します。  
  
1.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A>テキスト"testfunc"を使用します。  
  
2.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>です。  
  
3.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>です。  
  
4.  パーサー呼び出し<xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>です。