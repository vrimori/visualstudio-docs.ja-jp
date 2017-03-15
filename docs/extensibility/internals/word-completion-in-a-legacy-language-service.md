---
title: "従来の言語サービスでの単語の入力候補 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense の入力候補の言語サービス [マネージ パッケージ framework]"
  - "IntelliSense、入力候補"
  - "入力候補"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 従来の言語サービスでの単語の入力候補
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

単語の入力候補は、部分的に型指定された単語の文字がない場合に格納します。 1 つだけの補完候補があると、終了文字が入力されると、word は完了します。 単語の一部には、1 つ以上発生する可能性が一致すると、候補の一覧が表示されます。 入力候補の文字は、識別子の使用されていない任意の文字を使用できます。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。 [エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## 実装手順  
  
1.  ユーザーが選択すると **入力候補** から、 **IntelliSense** \] メニュー、 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> コマンドが言語サービスに送信します。  
  
2.  <xref:Microsoft.VisualStudio.Package.ViewFilter> クラスは、コマンド ウィンドウと呼び出しをキャッチ、 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 解析理由が付いているメソッド <xref:Microsoft.VisualStudio.Package.ParseReason>します。  
  
3.  <xref:Microsoft.VisualStudio.Package.Source> クラスの呼び出しでは、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 可能性がある単語の入力候補、ツール ヒント内の単語の一覧を使用して、表示の一覧を取得するメソッド、 <xref:Microsoft.VisualStudio.Package.CompletionSet> クラスです。  
  
     1 つだけに一致する単語がある場合、 <xref:Microsoft.VisualStudio.Package.Source> クラスという単語が完了するとします。  
  
 または、スキャナーがトリガー値を返す場合 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 識別子の最初の文字を入力すると、 <xref:Microsoft.VisualStudio.Package.Source> クラスは、これを検出し、呼び出し、 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 解析理由が付いているメソッド <xref:Microsoft.VisualStudio.Package.ParseReason>します。 ここでは、パーサーはメンバーの選択範囲の文字の存在を検出し、メンバーの一覧を指定する必要があります。  
  
## 入力候補のサポートを有効にします。  
 単語の入力候補のセットのサポートを有効にする、 `CodeSense` 名前付きパラメーターに渡される、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 言語パッケージに関連付けられているユーザーの属性です。 これにより設定、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> プロパティを <xref:Microsoft.VisualStudio.Package.LanguagePreferences> クラスです。  
  
 パーサーが解析理由値への応答の宣言の一覧を返す必要がある <xref:Microsoft.VisualStudio.Package.ParseReason>, 、動作するように word 完了します。  
  
## ParseSource メソッドの入力候補を実装します。  
 単語の候補の <xref:Microsoft.VisualStudio.Package.Source> クラスの呼び出し、 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> メソッドを <xref:Microsoft.VisualStudio.Package.AuthoringScope> 可能性がある単語の一致項目の一覧を取得するクラス。 派生したクラスで、リストを実装する必要があります、 <xref:Microsoft.VisualStudio.Package.Declarations> クラスです。 参照してください、 <xref:Microsoft.VisualStudio.Package.Declarations> クラスの詳細については、メソッドを実装する必要があります。  
  
 一覧には、1 つの単語が含まれている場合、 <xref:Microsoft.VisualStudio.Package.Source> クラスは、単語の一部の代わりにその単語を自動的に挿入します。 一覧には、複数の単語が含まれている場合、 <xref:Microsoft.VisualStudio.Package.Source> クラスは、ユーザーが適切な選択肢を選択ツール ヒントの一覧を表示します。  
  
 例を見ても、 <xref:Microsoft.VisualStudio.Package.Declarations> クラスの実装で [従来の言語サービスでのメンバーの完了](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)します。