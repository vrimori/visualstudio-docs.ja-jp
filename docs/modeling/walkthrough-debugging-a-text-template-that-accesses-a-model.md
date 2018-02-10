---
title: "チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d0cc9d59e4dfbe98312d44cceb91e729f0b81126
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ
変更またはドメイン固有言語ソリューションでテキスト テンプレートを追加するときに、エンジン ソース コードへ、または生成されたコードをコンパイルするときに、テンプレートを変換するときにエラーが発生する可能性があります。 次のチュートリアルでは、テキスト テンプレートのデバッグを行うことができます、処理の一部を示します。  
  
> [!NOTE]
>  を一般に、テンプレート文字列の詳細についてを参照してください[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)です。 テキスト テンプレートのデバッグの詳細については、次を参照してください。[チュートリアル: テキスト テンプレートのデバッグ](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f)です。  
  
## <a name="creating-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成します。  
 この手順では、次の特徴が含まれるドメイン固有言語ソリューションを作成します。  
  
-   名前: DebuggingTestLanguage  
  
-   ソリューション テンプレート: 最小言語  
  
-   ファイル拡張子: .ddd  
  
-   会社名: Fabrikam  
  
 ドメイン固有言語ソリューションを作成の詳細については、次を参照してください。[する方法: ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)です。  
  
## <a name="creating-a-text-template"></a>テキスト テンプレートの作成  
 テキスト テンプレートをソリューションに追加します。  
  
#### <a name="to-create-a-text-template"></a>テキスト テンプレートを作成するには  
  
1.  ソリューションをビルドし、デバッガーで実行を開始します。 (上、**ビルド** メニューのをクリックして**ソリューションのリビルド**、し、**デバッグ** メニューのをクリックして**デバッグの開始**)。Visual Studio の新しいインスタンスは、デバッグ プロジェクトを開きます。  
  
2.  という名前のテキスト ファイルを追加`DebugTest.tt`デバッグ プロジェクトにします。  
  
3.  確認して、**カスタム ツール**DebugTest.tt のプロパティに設定されて`TextTemplatingFileGenerator`です。  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>テキスト テンプレートから、モデルにアクセスするためのディレクティブのデバッグ  
 ステートメントと、テキスト テンプレートでの式からモデルにアクセスすることができます、生成されたディレクティブ プロセッサを呼び出す必要があります。 生成されたディレクティブ プロセッサを呼び出すことは、クラス、モデルでテキスト テンプレート コードで使用可能としてプロパティです。 詳細については、次を参照してください。[テキスト テンプレートからへのアクセス モデル](../modeling/accessing-models-from-text-templates.md)です。  
  
 次の手順では、正しくないディレクティブ名と正しくないプロパティ名をデバッグします。  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>正しくないディレクティブ名をデバッグするには  
  
1.  DebugTest.tt 内のコードを次のコードに置き換えます。  
  
    > [!NOTE]
    >  コードには、エラーが含まれています。 それをデバッグするために、エラーが導入されました。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**です。  
  
     **エラー一覧**ウィンドウには、このエラーが表示されます。  
  
     **'DebuggingTestLanguageDirectiveProcessor' という名前のプロセッサがディレクティブ 'modelRoot' をサポートしていません。変換は実行されません。**  
  
     この例では、ディレクティブの呼び出しには、正しくないディレクティブ名が含まれています。 指定した`modelRoot`ように、ディレクティブ名ですが正しいディレクティブ名は`DebuggingTestLanguage`します。  
  
3.  エラーをダブルクリックして、**エラー一覧**ウィンドウをコードにジャンプします。  
  
4.  コードを修正するには、ディレクティブ名を変更`DebuggingTestLanguage`です。  
  
     変更が強調表示されます。  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**です。  
  
     これで、システムでは、テキスト テンプレートを変換し、対応する出力ファイルを生成します。 内のエラーが表示されませんが、**エラー一覧**ウィンドウです。  
  
#### <a name="to-debug-an-incorrect-property-name"></a>正しくないプロパティ名をデバッグするには  
  
1.  DebugTest.tt 内のコードを次のコードに置き換えます。  
  
    > [!NOTE]
    >  コードには、エラーが含まれています。 それをデバッグするために、エラーが導入されました。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**です。  
  
     **エラー一覧**ウィンドウが表示され、これらのエラーのいずれかが表示されます。  
  
     (C#)  
  
     **変換をコンパイルして: Microsoft.VisualStudio.TextTemplating\<GUID > です。GeneratedTextTransformation' 'ExampleModel' の定義が含まれていません**  
  
     (Visual Basic)  
  
     **変換をコンパイルして: 'ExampleModel' がのメンバーではない ' Microsoft.VisualStudio.TextTemplating\<GUID > です。GeneratedTextTransformation' です。**  
  
     この場合、テキスト テンプレート コードには、正しくないプロパティ名が含まれています。 指定した`ExampleModel`名は、プロパティ名が正しいプロパティとして`LibraryModel`です。 正しいプロパティの名前を検索する、次のコードに示すように、パラメーターを提供します。  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  コードに移動する [エラー一覧] ウィンドウでエラーをダブルクリックします。  
  
4.  解決するには、コードを変更するプロパティ名を`LibraryModel`テキスト テンプレート コードにします。  
  
     変更が強調表示されます。  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**です。  
  
     これで、システムでは、テキスト テンプレートを変換し、対応する出力ファイルを生成します。 内のエラーが表示されませんが、**エラー一覧**ウィンドウです。