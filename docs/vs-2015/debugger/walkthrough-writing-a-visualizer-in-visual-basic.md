---
title: 'チュートリアル: Visual Basic でビジュアライザーを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e08059c18a7b5c1fff74539f4ba497c319838371
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881927"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>チュートリアル : Visual Basic でビジュアライザーを記述する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] を使用して簡単なビジュアライザーを作成する方法を説明します。 このチュートリアルで作成するビジュアライザーは、Windows フォーム メッセージ ボックスを使用して文字列の内容を表示します。 この単純な文字列のビジュアライザーは基本的な例で、プロジェクトに合わせて他のデータ型向けのビジュアライザーを作成するときに参考になります。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ヘルプの記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。 設定を変更するには、**ツール**メニュー選択**のインポートし、エクスポート**します。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 ビジュアライザー コードは、デバッガーによって読み取られる DLL に配置する必要があります。 最初の手順として、DLL のクラス ライブラリ プロジェクトを作成します。  
  
## <a name="create-and-prepare-a-class-library-project"></a>クラス ライブラリ プロジェクトの作成と準備  
  
#### <a name="to-create-a-class-library-project"></a>クラス ライブラリ プロジェクトを作成するには  
  
1. **ファイル**] メニューの [選択**新規**クリック**新しいプロジェクト**。  
  
2. **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類**s、 をクリックして**Visual Basic**します。  
  
3. **テンプレート**ボックスで、**クラス ライブラリ**します。  
  
4. **名前**など、クラス ライブラリの適切な名前の入力ボックスに、 **MyFirstVisualizer**します。  
  
5. **[OK]** をクリックします。  
  
   クラス ライブラリを作成したら、Microsoft.VisualStudio.DebuggerVisualizers.DLL への参照を追加することによって、この DLL で定義されているクラスを使用できるようにします。 ただし、最初にプロジェクトにわかりやすい名前を付けます。  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>Class1.vb の名前を変更して Microsoft.VisualStudio.DebuggerVisualizers に追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**Class1.vb**、ショートカット メニューのをクリックして**の名前を変更**します。  
  
2.  Class1.vb の名前を、DebuggerSide.vb などのわかりやすい名前に変更します。  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって、新しいファイル名に合わせて DebuggerSide.vb のクラス宣言が自動的に変更されます。  
  
3.  **ソリューション エクスプ ローラー**、右クリックして**My First Visualizer**、ショートカット メニューのをクリック**参照の追加**します。  
  
4.  **参照の追加** ダイアログ ボックスで、 **.NET**  タブで、Microsoft.VisualStudio.DebuggerVisualizers.DLL をクリックします。  
  
5.  **[OK]** をクリックします。  
  
6.  DebuggerSide.vb の `Imports` ステートメントに次のステートメントを追加します。  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## <a name="add-the-debugger-side-code"></a>デバッガー側のコードの追加  
 これで、デバッガー側のコードを作成する準備が整いました。 これは、視覚化を要する情報を表示するためにデバッガー内で実行されるコードです。 最初に、`DebuggerSide` オブジェクトの宣言を変更して、`DialogDebuggerVisualizer` 基底クラスを継承するようにする必要があります。  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>DialogDebuggerVisualizer から継承するには  
  
1. DebuggerSide.vb で、次のコード行に移動します。  
  
   ```  
   Public Class DebuggerSide  
   ```  
  
2. 次のようにコードを編集します。  
  
   ```  
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` には、オーバーライドする必要がある抽象メソッドが 1 つ (`Show`) あります。  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>DialogDebuggerVisualizer.Show メソッドをオーバーライドするには  
  
- `public class DebuggerSide` に、次のメソッドを追加します。  
  
  ```  
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  `Show` メソッドには、ビジュアライザーのダイアログ ボックス、または他のユーザー インターフェイスを実際に作成し、デバッガーからビジュアライザーに渡された情報を表示するコードを記述します。 したがって、このダイアログ ボックスを作成し、情報を表示するコードを追加する必要があります。 このチュートリアルでは、Windows フォーム メッセージ ボックスを使用します。 最初に、`Imports` の参照と <xref:System.Windows.Forms> ステートメントを追加する必要があります。  
  
#### <a name="to-add-systemwindowsforms"></a>System.Windows.Forms を追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックして**参照**、ショートカット メニューのをクリックして**参照の追加**します。  
  
2.  **参照の追加** ダイアログ ボックスで、 **.NET**  タブで  **System.Windows.Forms**。  
  
3.  **[OK]** をクリックします。  
  
4.  DebuggerSide.cs の `Imports` ステートメントに次のステートメントを追加します。  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>ビジュアライザーのユーザー インターフェイスの作成  
 次に、ビジュアライザーのユーザー インターフェイスを作成および表示するためのコードを追加します。 初めて作成するビジュアライザーであるため、ユーザー インターフェイスを簡素にし、メッセージ ボックスを使用します。  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>ビジュアライザーの出力をダイアログ ボックスに表示するには  
  
1.  `Show` メソッドに次のコード行を追加します。  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     このコード例には、エラー処理が含まれていません。 実際に使用するビジュアライザーなど、どのようなアプリケーションにも、エラー処理を追加する必要があります。  
  
2.  **ビルド** メニューのをクリックして**myfirstvisualizer のビルド**します。 プロジェクトが構築されます。 ビルド エラーを修正してから次の作業に進みます。  
  
## <a name="add-the-necessary-attribute"></a>必要な属性の追加  
 これで、デバッガー側のコードは終わりです。 ただし、もう 1 つ追加するものがあります。それは、ビジュアライザーを構成しているクラスのコレクションをデバッグ対象側に通知する属性です。  
  
#### <a name="to-add-the-debugee-side-code"></a>デバッギ側のコードを追加するには  
  
1.  DebuggerSide.vb の `Imports` ステートメントと `namespace MyFirstVisualizer` の間に次の属性コードを追加します。  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  **ビルド** メニューのをクリックして**myfirstvisualizer のビルド**します。 プロジェクトが構築されます。 ビルド エラーを修正してから次の作業に進みます。  
  
## <a name="create-a-test-harness"></a>テスト ハーネスの作成  
 これで、最初のビジュアライザーが完成しました。 手順どおりに作業を行ってきた場合は、ビジュアライザーを構築し、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] にインストールできます。 ただし、ビジュアライザーを [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] にインストールする前にテストを行い、ビジュアライザーが正しく動作することを確認する必要があります。 そこで、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] にインストールしないでビジュアライザーを実行する、テスト ハーネスを作成します。  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>ビジュアライザーを表示するテスト メソッドを追加するには  
  
1. 次のメソッドを `public DebuggerSide` クラスに追加します。  
  
   ```  
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. **ビルド** メニューのをクリックして**myfirstvisualizer のビルド**します。 プロジェクトが構築されます。 ビルド エラーを修正してから次の作業に進みます。  
  
   次に、ビジュアライザー DLL を呼び出す実行可能プロジェクトを作成する必要があります。 簡易にするために、コンソール アプリケーション プロジェクトを使用します。  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>ソリューションにコンソール アプリケーション プロジェクトを追加するには  
  
1. **ファイル** メニューのをクリックして**追加**、 をクリックし、**新しいプロジェクト**します。  
  
2. **新しいプロジェクトの追加**] ダイアログ ボックスで、**テンプレート**ボックスで、[**コンソール アプリケーション**します。  
  
3. **名前**ボックスに、コンソール アプリケーションのわかりやすい名前を入力します。 **MyTestConsole**します。  
  
4. **[OK]** をクリックします。  
  
   次に、必要な参照を追加して、MyTestConsole が MyFirstVisualizer を呼び出すことができるようにします。  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>必要な参照を MyTestConsole に追加するには  
  
1.  **ソリューション エクスプ ローラー**、右クリックして**MyTestConsole**、ショートカット メニューのをクリック**参照の追加**します。  
  
2.  **参照の追加** ダイアログ ボックスで、 **.NET**  タブで、Microsoft.VisualStudio.DebuggerVisualizers をクリックします。  
  
3.  **[OK]** をクリックします。  
  
4.  右クリック**MyTestConsole**、 をクリックし、**参照の追加**もう一度です。  
  
5.  **参照の追加**ダイアログ ボックスで、をクリックして、**プロジェクト**タブをクリックし、MyFirstVisualizer をクリックします。  
  
6.  **[OK]** をクリックします。  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>テスト ハーネスの終了とビジュアライザーのテスト  
 次に、コードを追加してテスト ハーネスを完成させます。  
  
#### <a name="to-add-code-to-mytestconsole"></a>コードを MyTestConsole に追加するには  
  
1. **ソリューション エクスプ ローラー**を右クリックして**Program.vb**、ショートカット メニューのをクリックして**の名前を変更**します。  
  
2. など、適切な Module1.vb の名前は編集**TestConsole.vb**します。  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] によって、新しいファイル名に合わせて TestConsole.vb のクラス宣言が自動的に変更されることに注意してください。  
  
3. でテスト コンソール。 vb では、次の追加`Imports`ステートメント。  
  
   ```  
   Imports MyFirstVisualizer  
   ```  
  
4. `Main` メソッドに、次のコードを追加します。  
  
   ```  
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   これで、作成したビジュアライザーをテストする準備が整いました。  
  
#### <a name="to-test-the-visualizer"></a>ビジュアライザーをテストするには  
  
1. **ソリューション エクスプ ローラー**、右クリックして**MyTestConsole**、ショートカット メニューのをクリック**スタートアップ プロジェクトとして設定**します。  
  
2. **デバッグ** メニューのをクリックして**開始**します。  
  
    コンソール アプリケーションが起動します。 ビジュアライザーが表示され、「Hello, World」という文字列が表示されます。  
  
   テストは成功です。 これで、最初のビジュアライザーの作成とテストが完了しました。  
  
   作成したビジュアライザーをテスト ハーネスから呼び出すのではなく、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] で使用する場合は、ビジュアライザーをインストールする必要があります。 詳細については、次を参照してください。[方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ビジュアライザーのアーキテクチャ](../debugger/visualizer-architecture.md)   
 [方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md)   
 [カスタム ビジュアライザーを作成する](../debugger/create-custom-visualizers-of-data.md)



