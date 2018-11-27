---
title: DLL プロジェクトのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96dc4277bfdc783d969a2e98fb93fcc5975e9ad7
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607628"
---
# <a name="debug-dlls-in-visual-studio"></a>Visual Studio で Dll をデバッグします。

DLL (ダイナミック リンク ライブラリ) は、コードとは、複数のアプリで使用できるデータを含むライブラリです。 作成、ビルド、構成するには、Visual Studio を使用して、Dll をデバッグできます。 

## <a name="create-a-dll"></a>DLL を作成します。

次の Visual Studio プロジェクト テンプレートには、Dll を作成できます。

- C#または Visual Basic クラス ライブラリ 
- C#または、Visual Basic Windows フォーム コントロール (WCF) ライブラリ 
- C++ のダイナミック リンク ライブラリ (DLL)

詳細については、次を参照してください。 [MFC のデバッグ手法](../debugger/mfc-debugging-techniques.md)します。

WCF ライブラリのデバッグは、クラス ライブラリのデバッグと似ています。 詳細については、次を参照してください。 [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)します。  

通常、別のプロジェクトから DLL を呼び出します。 DLL の構成に応じて、呼び出し元のプロジェクトをデバッグするときにステップ インし、DLL コードをデバッグできます。 

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL のデバッグ構成

Visual Studio プロジェクト テンプレートを使用して、アプリを作成する[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]デバッグとリリース ビルド構成の必要な設定を自動的に作成されます。 必要に応じて、これらの設定を変更できます。 詳細については、次の記事を参照してください。

- [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [プロジェクトの設定のC#デバッグ構成](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [方法: 構成セットのデバッグとリリース構成](../debugger/how-to-set-debug-and-release-configurations.md)  
  
### <a name="set-c-debuggableattribute"></a>C++ DebuggableAttribute を設定します。

C++ の DLL にアタッチするデバッガー、C++ コードを生成する必要があります`DebuggableAttribute`します。 

**設定する`DebuggableAttribute`:**

1. C++ DLL プロジェクトを選択**ソリューション エクスプ ローラー**を選択し、**プロパティ**アイコン、またはプロジェクトを右クリックし、選択**プロパティ**します。 
   
1. **プロパティ** ウィンドウで、**リンカー** > **デバッグ**を選択します**はい (/ASSEMBLYDEBUG)** の**デバッグできるアセンブリ**します。 

詳細については、次を参照してください。 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)します。  

### <a name="vxtskdebuggingdllprojectsexternal"></a> C/C++ DLL ファイルの場所を設定します。 

外部の DLL をデバッグするには、呼び出し元のプロジェクトで、DLL を検索できる必要があります、 [.pdb ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)、およびその他のファイル、DLL が必要です。 これらのファイルのコピー先のカスタム ビルド タスクを作成することができます、 *\<プロジェクト フォルダー > \Debug*出力フォルダー、またはファイルが手動でコピーできます。

C と C++ プロジェクトでは、それらを出力フォルダーにコピーする代わりに、プロジェクトのプロパティ ページで、ヘッダーおよび LIB ファイルの場所を設定できます。 

**C と C++ を設定するには、ヘッダーおよび LIB ファイルの場所。**

1. C/C++ DLL プロジェクトを選択**ソリューション エクスプ ローラー**を選択し、**プロパティ**アイコン、またはプロジェクトを右クリックし、選択**プロパティ**します。 
   
1. 上部にある、**プロパティ** ウィンドウで、**構成**を選択します**すべての構成**します。
   
1. **C/C++** > **全般** > **追加のインクルード ディレクトリ**、ヘッダー ファイルが含まれているフォルダーを指定します。
   
1. **リンカー** > **全般** > **追加のライブラリ ディレクトリ**、LIB ファイルが含まれているフォルダーを指定します。 
   
1. **リンカー** > **入力** > **追加の依存関係**、LIB ファイルのファイル名と完全なパスを指定します。

1. **[OK]** を選択します。

C++ プロジェクトの設定の詳細については、次を参照してください。[プロパティ ページ (Visual c)](/cpp/ide/property-pages-visual-cpp)します。
  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> デバッグ バージョンをビルドします。  

デバッグを開始する前に、DLL のデバッグ バージョンをビルドしてください。 DLL をデバッグするには、呼び出し元のアプリで検索できる必要があります、 [.pdb ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)とその他のすべてのファイル、DLL が必要です。 

DLL ファイルのコピー先のカスタム ビルド タスクを作成することができます、 *\<プロジェクト フォルダーを呼び出す > \Debug*出力フォルダー、またはファイルが手動でコピーできます。

必ず、正しい位置に、DLL を呼び出します。 当然のことがありますが、デバッガーが設定したブレークポイントをヒットしない場合、呼び出し元のアプリを検索して、別の DLL のコピーを読み込みます。 

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> DLL をデバッグします。  

DLL を直接実行することはできません。 呼び出す必要があります、アプリによっては、通常、 *.exe*ファイル。 詳細については、次を参照してください。[作成し、Visual c プロジェクトを管理](/cpp/ide/creating-and-managing-visual-cpp-projects)します。 

DLL をデバッグするには[呼び出し元のアプリからデバッグを開始](#vxtskdebuggingdllprojectsthecallingapplication)、または[DLL プロジェクトからデバッグ](how-to-debug-from-a-dll-project.md)その呼び出し元のアプリを指定することで。 デバッガーを使用することもできます。[イミディ エイト ウィンドウ](#vxtskdebuggingdllprojectstheimmediatewindow)DLL 関数またはメソッドを呼び出し元のアプリを使用せず、デザイン時に評価します。

詳細については、次を参照してください。[デバッガーで開始する](getting-started-with-the-debugger.md)します。

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> 呼び出し元のアプリからデバッグを開始します。

DLL を呼び出すアプリを指定できます。  
  
- アプリから、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]同じまたは別のソリューション、dll のプロジェクト。  
- 既にデプロイされている既存のアプリとテストまたは実稼働コンピューターで実行されています。  
- Web 上にあり、URL からアクセスします。  
- DLL を埋め込む web ページで web アプリです。  
  

呼び出し元のアプリから DLL をデバッグするには、次のことができます。  
  
- 呼び出し元のアプリのプロジェクトを開き、選択してデバッグを開始**デバッグ** > **デバッグの開始**キーを押して**F5**します。  

  または  

- 既に展開済みで、テストまたは実稼働コンピューター上で実行されているアプリにアタッチします。 Web サイトまたは web apps では、Dll のこのメソッドを使用します。 詳細については、次を参照してください。[方法: 実行中のプロセスにアタッチ](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)します。  
  
呼び出し元のアプリのデバッグを開始する前に、DLL で、ブレークポイントを設定します。 参照してください[ブレークポイントを使用して](../debugger/using-breakpoints.md)します。 DLL のブレークポイントにヒットしたときにすることができますコードをステップ実行、1 行ずつアクションを確認します。 詳細については、次を参照してください。[デバッガーでコード内を移動](../debugger/navigating-through-code-with-the-debugger.md)します。
  
デバッグ中に、使用することができます、**モジュール**Dll を確認するウィンドウおよび *.exe*ファイルをアプリの読み込み。 開くには、**モジュール**ウィンドウで、デバッグ中に、**デバッグ** > **Windows** > **モジュール**します。 詳細については、次を参照してください。[方法: [モジュール] ウィンドウを使用して、](../debugger/how-to-use-the-modules-window.md)します。 

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> イミディ エイト ウィンドウを使用します。  

使用することができます、**イミディ エイト**デザイン時に DLL の関数またはメソッドを評価するウィンドウ。 **イミディ エイト**ウィンドウは、呼び出し元のアプリの役割を果たします。 

>[!NOTE]
>使用することができます、**イミディ エイト**ほとんどの種類のプロジェクトでは、デザイン時のウィンドウ。 現在 .NET Core、SQL、または web プロジェクトのことができます。

たとえば、名前付きメソッドをテストする`Test`クラスで`Class1`:

1. DLL プロジェクトを開きを開き、**イミディ エイト**ウィンドウを選択して**デバッグ** > **Windows** > **イミディ エイト**キーを押して**Ctrl**+**Alt**+**は**します。  
   
1. 型のオブジェクトをインスタンス化`Class1`次を入力してC#でコードを**イミディ エイト**ウィンドウとキーを押して**Enter**します。 このマネージ コードが適してC#および Visual Basic で、適切な構文の変更と。  
   
   ```csharp
   Class1 obj = new Class1();  
   ```  
  
   C# では、すべての名前を完全修飾する必要があります。 任意のメソッドや変数は、言語サービスが、式を評価しようとしています。 現在のスコープとコンテキストでなければなりません。  
   
1. `Test` が 1 つの `int` パラメーターを受け取るものと想定し、 `Test` [イミディエイト] **ウィンドウを使用して** を評価します。  
   
   ```csharp
   ?obj.Test(10);  
   ```  
   
   結果の出力で、**イミディ エイト**ウィンドウ。  
   
1. デバッグを続行することができます`Test`内にブレークポイントを配置してもう一度、関数を評価します。  
   
   ブレークポイントにヒットして、ステップ`Test`します。 実行が終了後`Test`デバッガーがデザイン モードに戻しますされます。

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> 混合モードのデバッグ  

呼び出し元のアプリは、マネージまたはネイティブ コード内の DLL を記述できます。 マネージ DLL を呼び出すネイティブ アプリ、両方をデバッグする場合は、プロジェクトのプロパティで、マネージ コードとネイティブ デバッガーの両方を有効にすることができます。 実際のプロセスは、DLL プロジェクトまたは呼び出し元のアプリ プロジェクトからデバッグを開始するかどうかによって異なります。 詳細については、次を参照してください。[方法: 混合モードでデバッグ](../debugger/how-to-debug-in-mixed-mode.md)します。 

マネージ呼び出し元プロジェクトからネイティブ DLL をデバッグすることもできます。 詳細については、次を参照してください。[マネージ コードとネイティブ コードをデバッグする方法について](how-to-debug-managed-and-native-code.md)します。 

## <a name="see-also"></a>関連項目  
 [マネージ コードをデバッグします。](../debugger/debugging-managed-code.md)   
 [C++ プロジェクトのビジュアルの種類](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#、 F#、および Visual Basic プロジェクトの種類](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ デバッグ構成のプロジェクト設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [プロジェクトの設定のC#デバッグ構成](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic デバッグ構成のプロジェクトの設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)
