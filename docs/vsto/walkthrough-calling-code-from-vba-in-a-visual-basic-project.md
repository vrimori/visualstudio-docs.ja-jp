---
title: "チュートリアル : VBA から Visual Basic プロジェクトのコードを呼び出す"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ドキュメント [Visual Studio での Office 開発]、Visual Basic for Applications および"
  - "ThisDocument クラス"
  - "Word [Visual Studio での Office 開発]、呼び出し (コードを VBA から)"
  - "Visual Basic [Visual Studio での Office 開発]、呼び出し (コードを VBA から)"
  - "VBA [Visual Studio での Office 開発]、呼び出し (コードをドキュメント レベルのカスタマイズで)"
  - "Office ドキュメント [Visual Studio での Office 開発]、Visual Basic for Applications および"
  - "呼び出し (コードを VBA から)"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]、呼び出し (コードを)"
ms.assetid: 798bc2fa-449e-4d1a-86b4-18e57b02a4a8
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# チュートリアル : VBA から Visual Basic プロジェクトのコードを呼び出す
  このチュートリアルでは、ドキュメント内の Visual Basic for Applications \(VBA\) コードから Microsoft Office Word 用のドキュメント レベルのカスタマイズ内のメソッドを呼び出す方法を示します。 このプロシージャには次の 3 つの基本的な手順が含まれます。`ThisDocument` ホスト項目クラスにメソッドを追加する、VBA コードにメソッドを公開する、および、ドキュメント内の VBA コードからメソッドを呼び出す、の 3 つです。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 このチュートリアルでは具体的には Word を使用していますが、チュートリアルで示されるコンセプトは Excel のドキュメント レベルのプロジェクトにも適用されます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   VBA コードが含まれるドキュメントを作成する。  
  
-   Word のセキュリティ センターを使用して、ドキュメントの場所を信頼する。  
  
-   `ThisDocument` ホスト項目クラスにメソッドを追加する。  
  
-   VBA コードにメソッドを公開する。  
  
-   VBA コードからメソッドを呼び出す。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## VBA コードが含まれるドキュメントを作成する  
 最初の手順では、単純な VBA マクロを含むマクロ対応のドキュメントを作成します。 そのドキュメントに基づいた Visual Studio プロジェクトを作成する前に、ドキュメントに VBA プロジェクトを含める必要があります。 含めないと、Visual Studio は VBA プロジェクトを変更して、VBA コードがカスタマイズ アセンブリを呼び出せるようにすることができません。  
  
 使用する VBA コードを含むドキュメントが既にある場合は、この手順を省略できます。  
  
#### VBA コードが含まれるドキュメントを作成するには  
  
1.  Word を起動します。  
  
2.  作業中のドキュメントを **DocumentWithVBA** という名前で、Word の **マクロ有効文書 \(\*.docm\)** として保存します。 このドキュメントは、デスクトップなどの便利な場所に保存します。  
  
3.  リボンの **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
4.  **\[コード\]** グループの **\[Visual Basic\]** をクリックします。  
  
     Visual Basic エディターが開きます。  
  
5.  **\[プロジェクト\]** ウィンドウで、**\[ThisDocument\]** をダブルクリックします。  
  
     `ThisDocument` オブジェクトのコード ファイルが開きます。  
  
6.  コード ファイルに次の VBA コードを追加します。 このコードは何も実行しない単純な関数を定義します。 この関数の唯一の目的は、VBA プロジェクトがドキュメント内に確実に存在するようにすることです。 これは、このチュートリアルの後の手順に必要です。  
  
    ```  
    Sub EmptySub() End Sub  
    ```  
  
7.  ドキュメントを保存して、Word を終了します。  
  
## プロジェクトの作成  
 これで、先ほど作成したマクロ対応のドキュメントを使用する、Word のドキュメント レベルのプロジェクトを作成できます。  
  
#### 新しいプロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。 IDE が Visual Basic 開発設定を使用するように設定されている場合は、**\[ファイル\]** メニューの **\[新しいプロジェクト\]** をクリックします。  
  
3.  テンプレート ウィンドウで、**\[Visual Basic\]** を展開してから、**\[Office\/SharePoint\]** を展開します。  
  
4.  **\[Office アドイン\]** ノードを選択します。  
  
5.  プロジェクト テンプレートのリストで、**\[Word 2010 ドキュメント\]** または **\[Word 2013 ドキュメント\]** プロジェクトを選択します。  
  
6.  **\[名前\]** ボックスに、**「CallingCodeFromVBA」**と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード**が開きます。  
  
8.  **\[既存のドキュメントをコピーする\]** を選択し、**\[既存のドキュメントの完全なパス\]** ボックスで、先ほど作成した  **DocumentWithVBA** ドキュメントの場所を指定します。 独自のマクロ対応ドキュメントを使用している場合は、代わりにそのドキュメントの場所を指定します。  
  
9. **\[完了\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] はデザイナーで **DocumentWithVBA** ドキュメントを開き、**ソリューション エクスプローラー**に **CallingCodeFromVBA** プロジェクトを追加します。  
  
## ドキュメントの場所を信頼する  
 ソリューションのコードをドキュメント内の VBA コードに公開する前に、実行するドキュメント内の VBA を信頼する必要があります。 これにはいくつかの方法があります。 このチュートリアルでは、Word の**セキュリティ センター**で、ドキュメントの場所を信頼します。  
  
#### ドキュメントの場所を信頼するには  
  
1.  Word を起動します。  
  
2.  **\[ファイル\]** タブをクリックします。  
  
3.  **\[Word のオプション\]** ボタンをクリックします。  
  
4.  \[カテゴリ\] ウィンドウで **\[セキュリティ センター\]** をクリックします。  
  
5.  詳細ウィンドウで **\[セキュリティ センターの設定\]** をクリックします。  
  
6.  \[カテゴリ\] ウィンドウで **\[信頼できる場所\]** をクリックします。  
  
7.  詳細ウィンドウで **\[新しい場所の追加\]** をクリックします。  
  
8.  **\[Microsoft Office の信頼できる場所\]** ダイアログ ボックスで、**CallingCodeFromVBA** プロジェクトを含むフォルダーを参照します。  
  
9. **\[この場所のサブフォルダも信頼する\]** を選択します。  
  
10. **\[Microsoft Office の信頼できる場所\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
11. **\[セキュリティ センター\]** ダイアログ ボックスで **\[OK\]** をクリックします。  
  
12. **\[Word のオプション\]** ダイアログ ボックスで **\[OK\]** をクリックします。  
  
13. Word を終了します。  
  
## ThisDocument クラスにメソッドを追加する  
 VBA プロジェクトのセットアップができたので、今度は VBA コードから呼び出すことのできる `ThisDocument` ホスト項目クラスにメソッドを追加します。  
  
#### ThisDocument クラスにメソッドを追加するには  
  
1.  **ソリューション エクスプローラー**で **ThisDocument.vb** を右クリックし、**\[コードの表示\]** をクリックします。  
  
     コード エディターで **ThisDocument** ファイルが開きます。  
  
2.  `ThisDocument` クラスに次のメソッドを追加します。 このメソッドは、ドキュメントの先頭に 2 行 2 列の表を作成します。 パラメーターは、最初の行に表示されるテキストを指定します。 このチュートリアルの後半では、ドキュメント内の VBA コードからこのメソッドを呼び出します。  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CallingVBCustomizationFromVBA/VB/ThisDocument.vb#1)]  
  
3.  プロジェクトをビルドします。  
  
## VBA コードにメソッドを公開する  
 `CreateTable` メソッドをドキュメント内の VBA コードに公開するには、`ThisDocument` ホスト項目の **EnableVbaCallers** プロパティを **True** に設定します。  
  
#### メソッドを VBA コードに公開するには  
  
1.  **ソリューション エクスプローラー**で、**ThisDocument.vb** をダブルクリックします。  
  
     デザイナーで **DocumentWithVBA** ファイルが開きます。  
  
2.  **\[プロパティ\]** ウィンドウで、**EnableVbaCallers** プロパティを選択し、値を **True** に変更します。  
  
3.  表示されるメッセージで **\[OK\]** をクリックします。  
  
4.  プロジェクトをビルドします。  
  
## VBA コードからメソッドを呼び出す  
 これで、ドキュメント内の VBA コードから `CreateTable` メソッドを呼び出せます。  
  
> [!NOTE]  
>  このチュートリアルでは、プロジェクトのデバッグ中に VBA コードをドキュメントに追加します。 Visual Studio はビルド出力フォルダー内のドキュメントをメイン プロジェクト フォルダーからのドキュメントのコピーで置き換えるので、このドキュメントに追加したすべての VBA コードは次にプロジェクトをビルドすると上書きされます。 VBA コードを保存したい場合は、プロジェクト フォルダー内のドキュメントにコピーします。 詳細については、「[VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)」を参照してください。  
  
#### VBA コードからメソッドを呼び出すには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  **\[開発者\]** タブで、**\[コード\]** グループの、**\[Visual Basic\]** をクリックします。  
  
     Visual Basic エディターが開きます。  
  
3.  **\[挿入\]** メニューで **\[モジュール\]** をクリックします。  
  
4.  次のコードを新しいモジュールに追加します。  
  
     このコードはカスタマイズ アセンブリの `CreateTable` メソッドを呼び出します。 マクロは `ThisDocument` オブジェクトの `CallVSTOAssembly` プロパティを使用して、このメソッドにアクセスします。 このプロパティは、このチュートリアルで先ほど **EnableVbaCallers** プロパティを設定したときに自動的に生成されたものです。  
  
    ```  
    Sub CreateTable() Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date") End Sub  
    ```  
  
5.  F5 キーを押します。  
  
6.  新しい表がドキュメントに追加されたことを確認します。  
  
7.  変更を保存せずに Word を終了します。  
  
## 次の手順  
 Office ソリューションでの VBA からのコード呼び出しについて詳しくは、次のトピックを参照してください。  
  
-   VBA から Visual C\# カスタマイズのコードを呼び出します。 このプロセスは、Visual Basic のプロセスとは異なります。 詳細については、「[チュートリアル : VBA から Visual C&#35; プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)」を参照してください。  
  
-   VBA から VSTO アドインのコードを呼び出します。 詳細については、「[チュートリアル : VSTO アドインのコードを VBA から呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)」を参照してください。  
  
## 参照  
 [VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [方法 : Visual Basic プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [方法 : Visual C&#35; プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [チュートリアル : VBA から Visual C&#35; プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  