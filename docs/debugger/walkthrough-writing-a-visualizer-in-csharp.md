---
title: 'チュートリアル: ビジュアライザーを記述する (C#) |Microsoft Docs'
ms.custom: ''
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 12a2f16fcf96861df5f3c86f8fe44cb475b9ff23
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468495"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>チュートリアル : C# でビジュアライザーを記述する #
このチュートリアルでは、C# を使用して簡単なビジュアライザーを作成する方法を説明します。 このチュートリアルで作成するビジュアライザーは、Windows フォーム メッセージ ボックスを使用して文字列の内容を表示します。 この簡単な文字列ビジュアライザーは、それ自体ではそれほど役に立ちませんが、他のデータ型を表示する、より役に立つビジュアライザーを作成するために必要な基本手順として使用できます。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。 設定を変更するには、**ツール**メニュー選択**インポートおよびエクスポート設定**します。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 ビジュアライザー コードは、デバッガーによって読み取られる DLL に配置する必要があります。 このため、最初の手順として、DLL のクラス ライブラリ プロジェクトを作成します。  

## <a name="create-a-visualizer-manually"></a>ビジュアライザーを手動で作成します。

ビジュアライザーを作成するのには、次のタスクを実行します。
  
#### <a name="to-create-a-class-library-project"></a>クラス ライブラリ プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [選択**新規 > プロジェクト**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、 **Visual c#**、し、 **.NET Standard**します。  
  
3.  中央のペインで選択**クラス ライブラリ**します。  
  
4.  **名前**ボックスに、MyFirstVisualizer など、クラス ライブラリの適切な名前を入力します。  
  
5.  **[OK]** をクリックします。  
  
 クラス ライブラリを作成したら、Microsoft.VisualStudio.DebuggerVisualizers.DLL への参照を追加し、この DLL で定義されているクラスを使用できるようにします。 ただし、参照を追加する前に、クラス名をわかりやすい名前に変更する必要があります。  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.cs の名前を変更し Microsoft.VisualStudio.DebuggerVisualizers を追加するには  
  
1.  **ソリューション エクスプ ローラー**Class1.cs を右クリックし、選択、**の名前を変更**ショートカット メニューの します。  
  
2.  Class1.cs の名前を、DebuggerSide.cs などのわかりやすい名前に変更します。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] によって、新しいファイル名に合わせて DebuggerSide.cs のクラス宣言が自動的に変更されます。  
  
3.  **ソリューション エクスプ ローラー**、右クリック**参照**選択**参照の追加**ショートカット メニューの します。  
  
4.  **参照の追加** ダイアログ ボックスで、 **.NET**  タブで、Microsoft.VisualStudio.DebuggerVisualizers.DLL を選択します。  
  
5.  **[OK]** をクリックします。  
  
6.  DebuggerSide.cs の `using` ステートメントに次のステートメントを追加します。  
  
    ```csharp  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 これで、デバッガー側のコードを作成する準備が整いました。 これは、視覚化を要する情報を表示するためにデバッガー内で実行されるコードです。 最初に、`DebuggerSide` オブジェクトの宣言を変更して、`DialogDebuggerVisualizer` 基底クラスを継承するようにする必要があります。  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer から継承するには  
  
1.  DebuggerSide.cs で、次のコード行に移動します。  
  
    ```csharp  
    public class DebuggerSide  
    ```  
  
2.  コードを次のように変更します。  
  
    ```csharp  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` には、オーバーライドする必要がある抽象メソッドが 1 つ (`Show`) があります。  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show メソッドをオーバーライドするには  
  
-   `public class DebuggerSide`、次の追加**メソッド。**  
  
    ```csharp  
    protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 `Show` メソッドには、ビジュアライザーのダイアログ ボックス (または他のユーザー インターフェイス) を実際に作成し、デバッガーからビジュアライザーに渡された情報を表示するコードが格納されます。 したがって、このダイアログ ボックスを作成し、情報を表示するコードを追加する必要があります。 このチュートリアルでは、Windows フォーム メッセージ ボックスを使用します。 最初に、System.Windows.Forms の参照と `using` ステートメントを追加する必要があります。  
  
#### <a name="to-add-systemwindowsforms"></a>System.Windows.Forms を追加するには  
  
1.  **ソリューション エクスプ ローラー**、右クリック**参照**選択**参照の追加**ショートカット メニューの します。  
  
2.  **参照の追加** ダイアログ ボックスで、 **.NET**  タブで、System.Windows.Forms.DLL を選択します。  
  
3.  **[OK]** をクリックします。  
  
4.  DebuggerSide.cs の `using` ステートメントに次のステートメントを追加します。  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
 次に、ビジュアライザーのインターフェイスを作成し、表示するコードを追加します。 これは、初めて作成するビジュアライザーであるため、ユーザー インターフェイスを簡素にし、メッセージ ボックスを使用します。  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>ビジュアライザーの出力をダイアログ ボックスに表示するには  
  
1.  `Show` メソッドに次のコード行を追加します。  
  
    ```csharp  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     このコード例には、エラー処理が含まれていません。 実際に使用するビジュアライザーや、どのようなアプリケーションにも、エラー処理を追加する必要があります。  
  
2.  **ビルド** メニューの 選択**myfirstvisualizer のビルド**します。 プロジェクトが構築されます。 ビルド エラーを修正してから次の作業に進みます。  
  
 これで、デバッガー側のコードは終わりです。 ただし、もう 1 つ追加するものがあります。それは、ビジュアライザーを構成しているクラスのコレクションをデバッグ対象側に通知する属性です。  
  
#### <a name="to-add-the-debuggee-side-code"></a>デバッグ対象側のコードを追加するには  
  
1.  DebuggerSide.cs の `using` ステートメントと `namespace MyFirstVisualizer` の間に次の属性コードを追加します。  
  
    ```csharp  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target = typeof(System.String),  
    Description = "My First Visualizer")]  
    ```  
  
2.  **ビルド** メニューの 選択**myfirstvisualizer のビルド**します。 プロジェクトが構築されます。 ビルド エラーを修正してから次の作業に進みます。  
  
 これで、最初のビジュアライザーが完成しました。 手順どおりに作業を行ってきた場合は、ビジュアライザーを構築し、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にインストールできます。 ただし、ビジュアライザーを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にインストールする前にテストを行い、ビジュアライザーが正しく動作することを確認する必要があります。 そこで、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にインストールしないでビジュアライザーを実行する、テスト ハーネスを作成します。  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>ビジュアライザーを表示するテスト メソッドを追加するには  
  
1.  次のメソッドを `public DebuggerSide` クラスに追加します。  
  
    ```csharp  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  **ビルド** メニューの 選択**myfirstvisualizer のビルド**します。 プロジェクトが構築されます。 ビルド エラーを修正してから次の作業に進みます。  
  
 次に、ビジュアライザー DLL を呼び出す実行可能プロジェクトを作成する必要があります。 わかりやすくするために、コンソール アプリケーション プロジェクトを使用します。  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>ソリューションにコンソール アプリケーション プロジェクトを追加するには  
  
1.  **ファイル** メニューの 選択**追加** をクリックし、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクトの追加** ダイアログ ボックスで、選択**Visual c#** > **Windows デスクトップ**を選び、**コンソール アプリケーション**.  
  
3.  **名前**ボックスに、コンソール アプリケーションのわかりやすい名前を入力します。`MyTestConsole`します。  
  
4.  **[OK]** をクリックします。  
  
 次に、必要な参照を追加して、MyTestConsole が MyFirstVisualizer を呼び出すことができるようにします。  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>必要な参照を MyTestConsole に追加するには  
  
1.  **ソリューション エクスプ ローラー**、右クリックして**MyTestConsole**選択**参照の追加**ショートカット メニューの します。  
  
2.  **参照の追加**ダイアログ ボックスで、 **.NET**  タブで、Microsoft.VisualStudio.DebuggerVisualizers.DLL を選択します。  
  
3.  **[OK]** をクリックします。  
  
4.  右クリックして**MyTestConsole**選択**参照の追加**もう一度です。  
  
5.  **参照の追加**ダイアログ ボックスで、をクリックして、**プロジェクト**タブし、し、MyFirstVisualizer をクリックします。  
  
6.  **[OK]** をクリックします。  
  
 次に、コードを追加してテスト ハーネスを完成させます。  
  
#### <a name="to-add-code-to-mytestconsole"></a>コードを MyTestConsole に追加するには  
  
1.  **ソリューション エクスプ ローラー**Program.cs を右クリックし、選択、**の名前を変更**ショートカット メニューの します。  
  
2.  Program.cs の名前を、TestConsole.cs などの、よりわかりやすい名前に変更します。  
  
     **注**[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]自動的に新しいファイル名に合わせて TestConsole.cs のクラス宣言を変更します。  
  
3.  TestConsole.cs の `using` ステートメントに次のコードを追加します。  
  
    ```csharp  
    using MyFirstVisualizer;  
    ```  
  
4.  `Main` メソッドに、次のコードを追加します。  
  
    ```csharp  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 これで、作成したビジュアライザーをテストする準備が整いました。  
  
#### <a name="to-test-the-visualizer"></a>ビジュアライザーをテストするには  
  
1.  **ソリューション エクスプ ローラー**、右クリックして**MyTestConsole**選択**スタートアップ プロジェクトとして設定**ショートカット メニューの します。  
  
2.  **デバッグ**] メニューの [選択**開始**します。  
  
     コンソール アプリケーションが起動してビジュアライザーが表示され、"Hello, World" という文字列が表示されます。  
  
 テストは成功です。 これで、最初のビジュアライザーの作成とテストが完了しました。  
  
 作成したビジュアライザーをテスト ハーネスから呼び出すのではなく、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で使用する場合は、ビジュアライザーをインストールする必要があります。 詳細については、次を参照してください。[方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md)します。  
  
## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>ビジュアライザー項目テンプレートを使用して、ビジュアライザーを作成します。  
 このチュートリアルのこれまでの部分では、ビジュアライザーを手動で作成する方法について説明し、 これを演習形式で実行しました。 簡単なビジュアライザーがどのように動作するかを理解したことを踏まえて、ここでは、ビジュアライザー項目テンプレートを使用して、ビジュアライザーをより簡単に作成する方法を紹介します。  
  
 最初に、新しいクラス ライブラリ プロジェクトを作成する必要があります。  
  
#### <a name="to-create-a-new-class-library"></a>新しいクラス ライブラリを作成するには  
  
1.  **ファイル**] メニューの [選択**新規 > プロジェクト**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、 **Visual c#**、 **.NET Standard**します。  
  
3.  中央のペインで選択**クラス ライブラリ**します。   
  
4.  **名前**ボックスに、MySecondVisualizer など、クラス ライブラリの適切な名前を入力します。  
  
5.  **[OK]** をクリックします。  
  
 これで、ビジュアライザー項目を追加できます。  
  
#### <a name="to-add-a-visualizer-item"></a>ビジュアライザー項目を追加するには  
  
1.  **ソリューション エクスプ ローラー**、プロジェクト名を右クリックします。  
  
2.  ショートカット メニューで、**追加** をクリックし、**新しい項目の**します。  
  
3.  **新しい項目の追加**ダイアログ ボックスで、 **Visual c# アイテム**、**デバッガー ビジュアライザー**します。  
  
4.  **名前**ボックス SecondVisualizer.cs など、適切な名前を入力します。  
  
5.  **[追加]** をクリックします。  
  
 これで作業は完了です。 SecondVisualizer.cs ファイルを参照し、テンプレートによって追加されたコードを確認します。 さらにコードを実行してみてください。 以上で基礎的な項目を習得しました。これで、より複雑で有効な独自のビジュアライザーを作成できます。  
  
## <a name="see-also"></a>関連項目  
 [ビジュアライザーのアーキテクチャ](../debugger/visualizer-architecture.md)   
 [方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md)   
 [カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)
