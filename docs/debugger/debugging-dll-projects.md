---
title: "DLL プロジェクトのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッグ (DLL を)"
  - "テンプレート, DLL のデバッグ"
  - "DLL, デバッグ"
  - "[Visual Studio] のデバッグ, DLL"
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DLL プロジェクトのデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DLL を作成するテンプレートは次のとおりです。  
  
-   \(C\+\+、C\#、および Visual Basic\) クラス ライブラリ  
  
-   \(C\+\+、C\#、および Visual Basic\): Windows フォーム コントロール ライブラリ  
  
     Windows コントロール ライブラリのデバッグは、クラス ライブラリ プロジェクトのデバッグとほぼ同じです。 多くの場合、Windows コントロールは別のプロジェクトから呼び出します。 呼び出し元のプロジェクトをデバッグする場合は、Windows コントロールのコードにステップ インし、ブレークポイントを設定し、ほかのデバッグ操作を実行できます。 詳細については、「[Windows フォーム コントロール](../Topic/Windows%20Forms%20Controls.md)」を参照してください。  
  
-   \(C\# および Visual Basic\): Web コントロール ライブラリ  
  
     詳細については、「[Web コントロール ライブラリ \(マネージ コード\)](../debugger/web-control-library-managed-code.md)」を参照してください。  
  
-   \(C\+\+\): MFC ActiveX コントロールと MFC スマート デバイス ActiveX コントロール  
  
     ActiveX コントロールは、インターネット経由でクライアント コンピューターにダウンロードでき、Web ページで表示したり、アクティブにしたりできるコントロールです。  
  
     ActiveX コントロールは、スタンドアロンでは実行できず、HTML Web ページに埋め込む必要があるため、そのデバッグは他の種類のコントロールのデバッグと似ています。 詳細については、「[方法 : ActiveX コントロールをデバッグする](../debugger/how-to-debug-an-activex-control.md)」を参照してください。  
  
-   \(C\+\+\): MFC スマート デバイス DLL  
  
     詳細については、「[MFC のデバッグ技術](../debugger/mfc-debugging-techniques.md)」を参照してください。  
  
 このセクションでは、次のトピックについても説明します。  
  
-   [方法 : DLL プロジェクトからデバッグする](../debugger/how-to-debug-from-a-dll-project.md)  
  
-   [方法 : 混合モードでデバッグする](../debugger/how-to-debug-in-mixed-mode.md)  
  
 このトピックは次の内容で構成されており、クラス ライブラリ デバッグの準備に関する考慮事項について説明しています。  
  
-   [デバッグ バージョンのビルド](#vxtskdebuggingdllprojectsbuildingadebugversion)  
  
-   [混合モードのデバッグ](#vxtskdebuggingdllprojectsmixedmodedebugging)  
  
-   [既定の構成の変更](#vxtskdebuggingdllprojectschangingdefaultconfigurations)  
  
-   [DLL のデバッグ方法](#vxtskdebuggingdllprojectswaystodebugthedll)  
  
-   [呼び出し元のアプリケーション](#vxtskdebuggingdllprojectsthecallingapplication)  
  
-   [Web ページ上のコントロール](#vxtskdebuggingdllprojectscontrolsonawebpage)  
  
-   [&#91;イミディエイト&#93; ウィンドウ](#vxtskdebuggingdllprojectstheimmediatewindow)  
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> デバッグ バージョンのビルド  
 デバッグをどの方法で始める場合でも、DLL のデバッグ バージョンを先にビルドして、アプリケーションが参照する場所にデバッグ バージョンを配置するようにします。 この手順を忘れると、アプリケーションが別のバージョンの DLL を参照して読み込む可能性があります。 その場合、ブレークポイントがヒットせず、プログラムの実行が継続されます。 デバッグ時には、デバッガーの **\[モジュール\]** ウィンドウを開いて、プログラムが読み込んだ DLL を確認できます。**\[モジュール\]** ウィンドウには、デバッグしているプロセスに読み込まれた DLL や EXE が一覧表示されます。 詳細については、「[方法 : \[モジュール\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Modules%20Window.md)」を参照してください。  
  
 C\+\+ で記述されたコードにデバッガーをアタッチするには、コードが `DebuggableAttribute` を生成する必要があります。[\/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) リンカー オプションを使ってリンクすると、これを自動的にコードに追加できます。  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 混合モードのデバッグ  
 DLL を呼び出す呼び出し元のアプリケーションは、マネージ コードで記述されている場合と、ネイティブ コードで記述されている場合があります。 マネージ DLL とそれを呼び出すネイティブ コードの両方をデバッグする場合は、マネージ デバッガーとネイティブ デバッガーを共に有効にする必要があります。 これは、**\[\<プロジェクト\> プロパティ ページ\]** ダイアログ ボックスで選択できます。 DLL プロジェクトからデバッグを開始するか、呼び出し元のアプリケーション プロジェクトからデバッグを開始するかによって、確認方法は異なります。 詳細については、「[方法 : 混合モードでデバッグする](../debugger/how-to-debug-in-mixed-mode.md)」を参照してください。  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> 既定の構成の変更  
 プロジェクト テンプレートを使用してコンソール アプリケーション プロジェクトを作成するときは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] により、デバッグ構成とリリース構成に必要な設定が自動的に作成されます。 これらの設定は必要に応じて変更できます。 詳細については、「[C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)」、「[C\# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)」、「[Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)」、および「[方法 : デバッグ構成とリリース構成を設定する](../debugger/how-to-set-debug-and-release-configurations.md)」を参照してください。  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> DLL のデバッグ方法  
 このセクションの各プロジェクトでは、DLL を作成します。 DLL は直接実行できず、アプリケーション \(通常は EXE\) から呼び出す必要があります。 詳細については、「[Visual C\+\+ プロジェクトの作成および管理](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)」を参照してください。 呼び出し元のアプリケーションは、次の条件のいずれかに該当している場合があります。  
  
-   クラス ライブラリを格納する同じ [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソリューション内の、別のプロジェクトにビルドされたアプリケーション  
  
-   テスト コンピューターや運用コンピューターに既に配置されている既存のアプリケーション  
  
-   Web に配置され、URL からアクセスするアプリケーション  
  
-   DLL を埋め込む Web ページを含む Web アプリケーション  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 呼び出し元のアプリケーションのデバッグ  
 DLL をデバッグするには、まず呼び出し元のアプリケーション \(通常、EXE または Web アプリケーション\) をデバッグします。 これには、複数の方法があります。  
  
-   呼び出し元のアプリケーションに対するプロジェクトが存在する場合は、そのプロジェクトを開いて、**\[デバッグ\]** メニューから実行を開始できます。 詳細については、「[How to: Start Execution](http://msdn.microsoft.com/ja-jp/b0fe0ce5-900e-421f-a4c6-aa44ddae453c)」を参照してください。  
  
-   呼び出し元のアプリケーションが、テスト コンピューターや運用コンピューターに配置されている既存のプログラムであり、既に動作している場合は、それにアタッチできます。 DLL が Internet Explorer によってホストされるコントロール、または Web ページ上のコントロールである場合は、この方法を使用します。 詳細については、「[How to: Attach to a Running Process](http://msdn.microsoft.com/ja-jp/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)」を参照してください。  
  
-   DLL プロジェクトからデバッグできます。 詳細については、「[方法 : DLL プロジェクトからデバッグする](../debugger/how-to-debug-from-a-dll-project.md)」を参照してください。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の**イミディエイト** ウィンドウからデバッグできます。 この場合、**イミディエイト** ウィンドウは、アプリケーションの役割をします。  
  
 呼び出し元のアプリケーションのデバッグを始める前に、通常はクラス ライブラリ内にブレークポイントを設定します。 詳細については、「[Breakpoints and Tracepoints](http://msdn.microsoft.com/ja-jp/fe4eedc1-71aa-4928-962f-0912c334d583)」を参照してください。 ブレークポイントにヒットした場合は、コードのステップ実行により、1 行ずつアクションを確認して問題を特定できます。 詳細については、「[Code Stepping Overview](http://msdn.microsoft.com/ja-jp/8791dac9-64d1-4bb9-b59e-8d59af1833f9)」を参照してください。  
  
###  <a name="vxtskdebuggingdllprojectscontrolsonawebpage"></a> Web ページ上のコントロール  
 Web ページ コントロールをデバッグするには、それを埋め込む [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ページを作成します \(このようなページがまだ存在しない場合\)。 次に、Web ページ コードとコントロール コードにブレークポイントを設定します。 Web ページを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] から起動します。  
  
 呼び出し元のアプリケーションのデバッグを始める前に、通常は DLL 内にブレークポイントを設定します。 ブレークポイントにヒットした場合は、コードのステップ実行により、1 行ずつアクションを確認して問題を特定できます。 詳細については、「[Breakpoints and Tracepoints](http://msdn.microsoft.com/ja-jp/fe4eedc1-71aa-4928-962f-0912c334d583)」を参照してください。  
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> \[イミディエイト\] ウィンドウ  
 DLL の関数やメソッドは、呼び出し元のアプリケーションがなくても評価できます。 そのためには、**\[イミディエイト\]** ウィンドウを使用して、デザイン時デバッグを行います。 この方法でデバッグするには、DLL プロジェクトが開いているときに次の手順を実行します。  
  
1.  デバッガーの **\[イミディエイト\]** ウィンドウを開きます。  
  
2.  `Test` クラスの `Class1` メソッドをテストする場合は、次の C\# コードを \[イミディエイト\] ウィンドウで入力して、`Class1` 型のオブジェクトをインスタンス化します。 このマネージ コードは、構文を適切に変更することで Visual Basic と C\+\+ で動作します。  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     C\# では、すべての名前を完全修飾する必要があります。 また、メソッドや変数はいずれもデバッグ セッションの現在のスコープとコンテキストに含まれる必要があります。  
  
3.  `Test` が 1 つの `int` パラメーターを受け取るものと想定し、**\[イミディエイト\]** ウィンドウを使用して `Test` を評価します。  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     結果が **\[イミディエイト\]** ウィンドウに出力されます。  
  
4.  `Test` の中にブレークポイントを配置し、関数を再び評価してデバッグを継続できます。  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     ブレークポイントにヒットすると、`Test` をステップ実行できます。`Test` の実行が終了すると、デバッガーはデザイン モードに戻ります。  
  
## 参照  
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)   
 [Visual C\+\+ プロジェクトの種類](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C\#、F\#、および Visual Basic のプロジェクト](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C\+\+ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C\# デバッグ構成のプロジェクト設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)