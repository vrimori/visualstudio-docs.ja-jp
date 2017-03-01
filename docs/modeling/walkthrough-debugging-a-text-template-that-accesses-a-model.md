---
title: "チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7bbe2b592dc315bc0885e1f1ca4c890e4e66255d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>チュートリアル: モデルにアクセスするテキスト テンプレートのデバッグ
変更またはドメイン固有言語ソリューションでテキスト テンプレートを追加すると、エンジンのソース コードに、または生成されたコードをコンパイルするときにテンプレートを変換するときにエラーが発生する可能性があります。 次のチュートリアルでは、テキスト テンプレートをデバッグすることの一部を示します。  
  
> [!NOTE]
>  テンプレート文字列の詳細については「一般に、[コードの生成と T4 テキスト テンプレート](../modeling/code-generation-and-t4-text-templates.md)します。 テキスト テンプレートのデバッグの詳細については、次を参照してください。[チュートリアル: テキスト テンプレートのデバッグ](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f)します。  
  
## <a name="creating-a-domain-specific-language-solution"></a>ドメイン固有言語ソリューションを作成します。  
 この手順では、次の特徴が含まれるドメイン固有言語ソリューションを作成します。  
  
-   名前: DebuggingTestLanguage  
  
-   ソリューション テンプレート: 最小言語  
  
-   ファイル拡張子: .ddd  
  
-   会社名: Fabrikam  
  
 ドメイン固有言語ソリューションの作成の詳細については、次を参照してください。[方法: ドメイン固有言語ソリューションを作成する](../modeling/how-to-create-a-domain-specific-language-solution.md)です。  
  
## <a name="creating-a-text-template"></a>テキスト テンプレートを作成します。  
 テキスト テンプレートをソリューションに追加します。  
  
#### <a name="to-create-a-text-template"></a>テキスト テンプレートを作成するには  
  
1.  ソリューションをビルドし、デバッガーで実行を開始します。 (上、**ビルド** メニューのをクリックして**ソリューションのリビルド**、し、**デバッグ** メニューのをクリックして**デバッグ開始**)。Visual Studio の新しいインスタンスは、デバッグ プロジェクトを開きます。  
  
2.  という名前のテキスト ファイルを追加`DebugTest.tt`デバッグ プロジェクトにします。  
  
3.  確認して、**カスタム ツール**DebugTest.tt のプロパティに設定されて`TextTemplatingFileGenerator`します。  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>テキスト テンプレートからモデルにアクセスするためのディレクティブのデバッグ  
 モデルにアクセスするには、ステートメントとテキスト テンプレート内の式から、前に、生成されたディレクティブ プロセッサを最初に呼び出す必要があります。 生成されたディレクティブ プロセッサを呼び出し、クラス、モデル内を可能テキスト テンプレート コード プロパティとして。 詳細については、次を参照してください。[テキスト テンプレートからへのアクセス モデル](../modeling/accessing-models-from-text-templates.md)します。  
  
 次の手順では、ディレクティブ名の間違い、不適切なプロパティ名をデバッグします。  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>ディレクティブ名の間違いをデバッグするには  
  
1.  DebugTest.tt 内のコードを次のコードに置き換えます。  
  
    > [!NOTE]
    >  コードには、エラーが含まれています。 それをデバッグするために、エラーが導入されました。  
  
    ```c#  
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
  
    ```vb#  
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
  
2.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     **エラー一覧**ウィンドウには、このエラーが表示されます。  
  
     **'DebuggingTestLanguageDirectiveProcessor' という名前のプロセッサは、'modelRoot' という名前のディレクティブをサポートしていません。変換は実行されません。**  
  
     この場合は、ディレクティブの呼び出しには、ディレクティブ名間違いにはが含まれています。 指定した`modelRoot`ように、ディレクティブ名ですが正しいディレクティブの名前は`DebuggingTestLanguage`です。  
  
3.  エラーをダブルクリックして、**エラー一覧**コードに移動するウィンドウです。  
  
4.  ディレクティブの名前を変更する、コードを修正する`DebuggingTestLanguage`です。  
  
     変更が強調表示されます。  
  
    ```c#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     今すぐ、システムでは、テキスト テンプレートを変換し、対応する出力ファイルが生成されます。 エラーが表示されませんが、**エラー一覧**ウィンドウです。  
  
#### <a name="to-debug-an-incorrect-property-name"></a>間違ったプロパティ名をデバッグするには  
  
1.  DebugTest.tt 内のコードを次のコードに置き換えます。  
  
    > [!NOTE]
    >  コードには、エラーが含まれています。 それをデバッグするために、エラーが導入されました。  
  
    ```c#  
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
  
    ```vb#  
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
  
2.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     **エラー一覧**ウィンドウが表示され、これらのエラーのいずれかが表示されます。  
  
     (C#)  
  
     **変換をコンパイルして: Microsoft.VisualStudio.TextTemplating\<GUID > します。GeneratedTextTransformation' 'ExampleModel' の定義が含まれていません。**  
  
     (Visual Basic)  
  
     **変換をコンパイルして: 'ExampleModel' は、メンバーではない ' Microsoft.VisualStudio.TextTemplating\<GUID > します。GeneratedTextTransformation' です。**  
  
     この場合、テキスト テンプレート コードには、不適切なプロパティ名が含まれています。 指定した`ExampleModel`名は、プロパティ名が、適切なプロパティとして`LibraryModel`します。 適切なプロパティの名前を検索する、次のコードに示すように、パラメーターを提供します。  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  コードに移動する [エラー一覧] ウィンドウでエラーをダブルクリックします。  
  
4.  プロパティ名を変更する、コードを修正する`LibraryModel`テキスト テンプレート コードにします。  
  
     変更が強調表示されます。  
  
    ```c#  
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
  
    ```vb#  
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
  
5.  **ソリューション エクスプ ローラー**DebugTest.tt を右クリックし、クリックして**カスタム ツールの実行**します。  
  
     今すぐ、システムでは、テキスト テンプレートを変換し、対応する出力ファイルが生成されます。 エラーが表示されませんが、**エラー一覧**ウィンドウです。
