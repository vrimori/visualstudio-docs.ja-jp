---
title: "[コンパイル] ページ、プロジェクト デザイナー (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesCompile"
helpviewer_keywords: 
  - "コンパイル、Visual Basic プロパティ"
  - "コンパイル、オプション [Visual Basic]"
  - "コンパイラ、Visual Basic オプション"
  - "コンパイル、命令 [Visual Basic]"
  - "コンパイラ オプション、Visual Basic"
  - "プロジェクト デザイナー、[コンパイル] ページ"
  - "[コンパイル] ページ (プロジェクト デザイナーの)"
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 60
caps.handback.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# [コンパイル] ページ、プロジェクト デザイナー (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コンパイル命令を指定するには、プロジェクト デザイナーの **\[コンパイル\]** ページを使用します。  このページでは、詳細なコンパイラ オプションや、ビルド前のイベントまたはビルド後のイベントを指定することもできます。  
  
 **\[コンパイル\]** のページにアクセスするには、**\[ソリューション エクスプローラー\]** のプロジェクト ノード \(ない **\[ソリューション\]** ノード\) を選択します。  その後、**プロジェクト**、メニュー バーの **\[プロパティ\]** を選択します。  プロジェクト デザイナーが表示されたら、**\[コンパイル\]** タブをクリックします。  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## 構成およびプラットフォーム  
 次の設定を使用すると、表示または変更する構成とプラットフォームを選択できます。  
  
> [!NOTE]
>  簡易ビルド構成を使用した場合、デバッグ バージョンとリリース バージョンのどちらをビルドするかの決定はプロジェクト システムによって行われます。  そのため、**\[構成\]** および **\[プラットフォーム\]** の一覧は表示されません。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
 **構成**  
 表示または変更する構成設定を指定します。  設定は、**\[Debug\]** \(既定\)、**\[Release\]**、または **\[すべての構成\]** です。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」および「[方法 : 構成を作成および編集する](../../ide/how-to-create-and-edit-configurations.md)」を参照してください。  
  
 **プラットフォーム**  
 表示または変更するプラットフォーム設定を指定します。  **\[Any CPU\]** \(既定\)、**\[x64\]**、または **\[x86\]** を指定できます。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
## コンパイラ構成オプション  
 次の設定では、コンパイラ構成オプションを設定できます。  
  
 **\[ビルド出力パス\]**  
 このプロジェクト構成の出力ファイルの場所を指定します。  このボックスにビルド出力のパスを入力するか、**\[参照\]** をクリックしてパスを選択します。  このパスは、相対パスであることに注意してください。絶対パスを入力しても、相対パスとして保存されます。  既定のパスは bin\\Debug\\ or bin\\Release\\ です。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
 簡易ビルド構成を使用した場合、デバッグ バージョンとリリース バージョンのどちらをビルドするかの決定はプロジェクト システムによって行われます。  **\[デバッグ\]** メニューの **\[ビルド\]** コマンド \(F5\) を使用すると、指定した **\[出力パス\]** に関係なく、デバッグ用の場所にビルドが配置されます。  ただし、**\[ビルド\]** メニューの **\[ビルド\]** コマンドでは、指定した場所にビルドが配置されます。  詳細については、「[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)」を参照してください。  
  
 **\[Option Explicit\]**  
 変数の暗黙宣言を許可するかどうかを指定します。  **\[On\]** をクリックすると、変数の明示的な宣言が必要になります。  宣言されていない変数を使用している場合、コンパイラによってエラーが報告されます。  変数の暗黙の宣言を許可する場合は、**\[Off\]** をクリックします。  
  
 この設定は、[\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) コンパイラ オプションに対応します。  
  
 ソース コード ファイルに [Option Explicit Statement](/dotnet/visual-basic/language-reference/statements/option-explicit-statement) が含まれている場合、ステートメント内の `On` または `Off` の値は、**\[コンパイル\]** ページの **\[Option Explicit\]** 設定をオーバーライドします。  
  
 新しいプロジェクトを作成するとき、**\[コンパイル\]** ページの **\[Option Explicit\]** 設定は、**\[オプション\]** ダイアログ ボックスの **\[Option Explicit\]** 設定の値に設定されます。  このダイアログ ボックスの設定値を表示または変更するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスで、**\[プロジェクトおよびソリューション\]** を展開し、**\[Visual Basic の既定値\]** をクリックします。  **\[Visual Basic の既定値\]** の **\[Option Explicit\]** の既定の初期設定は **\[On\]** です。  
  
 一般的に、**\[Option Explicit\]** を `Off` に設定することは適切な方法ではありません。  1 つ以上の場所で変数名のスペルを間違えると、プログラムの実行時に予期しない結果が生じる可能性があります。  
  
 **\[Option Strict\]**  
 厳密な型指定規則を適用するかどうかを指定します。  **\[Option Strict\]** が **\[On\]** の場合に、コンパイル時エラーの原因となる条件を次に示します。  
  
-   暗黙の縮小変換  
  
-   遅延バインディング  
  
-   `Object` 型になる暗黙的な型指定  
  
 暗黙的なデータ型変換が縮小変換である場合、暗黙の縮小変換エラーが発生します。  詳細については、「[Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)」、「[Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)」、および「[Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)」を参照してください。  
  
 `Object` 型として宣言された変数のプロパティまたはメソッドに代入されるオブジェクトは、遅延バインディングされます。  詳細については、「[Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)」および「[Early and Late Binding](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding)」を参照してください。  
  
 宣言された変数の適切な型を推論できず、`Object` の型が推論された場合、暗黙のオブジェクト型エラーが発生します。  このエラーは主に、`As` 句を使用せずに `Dim` ステートメントを使用して変数を宣言し、`Option Infer` が Off である場合に発生します。  詳細については、「[Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)」、「[Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)」、および「[Visual Basic Language Specification](/dotnet/visual-basic/reference/language-specification)」を参照してください。  
  
 **\[Option Strict\]** 設定は、[\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) コンパイラ オプションに対応します。  
  
 ソース コード ファイルに [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) が含まれている場合、ステートメント内の `On` または `Off` の値は、**\[コンパイル\]** ページの **\[Option Strict\]** 設定をオーバーライドします。  
  
 プロジェクトを作成するとき、**\[コンパイル\]** ページの **\[Option Strict\]** 設定は、**\[オプション\]** ダイアログ ボックスの **\[Option Strict\]** 設定の値に設定されます。  このダイアログ ボックスの設定値を表示または変更するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスで、**\[プロジェクトおよびソリューション\]** を展開し、**\[Visual Basic の既定値\]** をクリックします。  **\[Visual Basic の既定値\]** の **\[Option Strict\]** の既定の初期設定は **\[Off\]** です。  
  
 **Option Strict の個々の警告。 \[コンパイル\]** ページの **\[警告の構成\]** セクションには、`Option Strict` が On のときにコンパイル時エラーの原因となる 3 つの条件に対応する設定があります。  その 3 つの設定を次に示します。  
  
-   **暗黙の型変換**  
  
-   **遅延バインディング \(呼び出しは実行時に失敗することがある\)**  
  
-   **暗黙の型 \(想定されるオブジェクト\)**  
  
 **\[Option Strict\]** を **\[On\]** に設定すると、この 3 つの警告の構成の設定はすべて、**\[エラー\]** に設定されます。  **\[Option Strict\]** を **\[Off\]** に設定すると、これらの設定はすべて、**\[なし\]** に設定されます。  
  
 警告の構成の設定を、それぞれ個別に **\[なし\]**、**\[警告\]**、または **\[エラー\]** に変更できます。  この 3 つの警告の構成の設定をすべて **\[エラー\]** に設定すると、`Option strict` ボックスに `On` が表示されます。  すべて **\[なし\]** に設定すると、このボックスには `Off` が表示されます。  これらの設定を他の組み合わせにした場合は、**\[\(カスタム\)\]** が表示されます。  
  
 **\[Option Compare\]**  
 使用する文字列比較の種類を指定します。  大文字小文字を区別するバイナリの文字列比較を使用するようにコンパイラに指示する場合は、**\[バイナリ\]** をクリックします。  ロケール固有の大文字小文字を区別しないテキスト文字列比較を使用する場合は、**\[テキスト\]** をクリックします。  
  
 この設定は、[\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) コンパイラ オプションに対応します。  
  
 ソース コード ファイルに [Option Compare Statement](/dotnet/visual-basic/language-reference/statements/option-compare-statement) が含まれている場合、ステートメント内の `Binary` または `Text` の値は、**\[コンパイル\]** ページの **\[Option Compare\]** 設定をオーバーライドします。  
  
 プロジェクトを作成するとき、**\[コンパイル\]** ページの **\[Option Compare\]** 設定は、**\[オプション\]** ダイアログ ボックスの **\[Option Compare\]** 設定の値に設定されます。  このダイアログ ボックスの設定値を表示または変更するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスで、**\[プロジェクトおよびソリューション\]** を展開し、**\[Visual Basic の既定値\]** をクリックします。  **\[Visual Basic の既定値\]** の **\[Option Compare\]** の既定の初期設定は **\[バイナリ\]** です。  
  
 **\[Option Infer\]**  
 変数の宣言でローカル型の推論を許可するかどうかを指定します。  ローカル型推論を許可するには、**\[On\]** を選択します。  ローカル型の推定を禁止するには、**\[Off\]** を選択します。  
  
 この設定は、[\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) コンパイラ オプションに対応します。  
  
 ソース コード ファイルに [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement) が含まれている場合、ステートメント内の `On` または `Off` の値は、**\[コンパイル\]** ページの **\[Option Infer\]** 設定をオーバーライドします。  
  
 プロジェクトを作成するとき、**\[コンパイル\]** ページの **\[Option Infer\]** 設定は、**\[オプション\]** ダイアログ ボックスの **\[Option Infer\]** 設定の値に設定されます。  このダイアログ ボックスの設定値を表示または変更するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスで、**\[プロジェクトおよびソリューション\]** を展開し、**\[Visual Basic の既定値\]** をクリックします。  **\[Visual Basic の既定値\]** の **\[Option Infer\]** の既定の初期設定は **\[On\]** です。  
  
 **対象の CPU**  
 出力ファイルがターゲットとするプロセッサを指定します。  どのプロセッサでもかまわないことを指定する場合は、各 32 ビット Intel 互換プロセッサの場合はを **\[x86\]**、任意の 64 ビット Intel 互換プロセッサの **\[x64\]**、ARM のプロセッサの **\[ARM\]**、または **\[Any CPU\]** を指定します。  **\[Any CPU\]** はハードウェアの種類の最大数で実行されるアプリケーションを使用することにより、新しいプロジェクトの既定値です。  
  
 詳細については、「[\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform)」を参照してください。  
  
 **\[32 ビットの優先\]**  
 **\[Prefer32\-bit\]** のチェック ボックスがオンの場合、アプリケーションは Windows の 32 ビット バージョンと 64 ビット バージョンの 32 ビット アプリケーションとして実行されます。  それ以外の場合、アプリケーションは Windows の 32 ビット バージョンで 32 ビット アプリケーションと 64 ビット バージョンの Windows で 64 ビット アプリケーションとして実行されます。  
  
 64 ビット アプリケーションはポインターのサイズを重複するため、実行し、排他的に 32 ビットのライブラリに互換性の問題が発生する可能性があります。  これは、実行速度は、メモリの 4 つ以上の GB が必要な場合にのみ、64 ビットの方法でアプリケーションを実行すると便利です。  
  
 このチェック ボックスは、次の条件がすべて満たされた場合だけです:  
  
-   **\[Compile Page\]** で、**\[対象の CPU \(T\]** の一覧が **\[Any CPU\]** に設定されます。  
  
-   **\[アプリケーション ページ\]** で、**\[アプリケーションの種類\]** のリストでは、プロジェクトのアプリケーションであることを指定します。  
  
-   **\[アプリケーション ページ\]** で、**\[ターゲット フレームワーク\]** の一覧は、.NET Framework 4.5 を指定します。  
  
 **\[警告の構成\]**  
 このテーブルには、ビルド条件の一覧と、各条件に対応する通知レベル \(**\[なし\]**、**\[警告\]**、または **\[エラー\]**\) が表示されます。  
  
 既定では、コンパイラの警告すべてが、コンパイル時にタスク一覧に追加されます。  コンパイラが警告やエラーを発行しないようにするには、**\[すべての警告を表示しない\]** を選択します。  コンパイラが警告を解決が必要なエラーとして扱うようにするには、**\[すべての警告をエラーとして扱う\]** を選択します。  
  
 **\[すべての警告を表示しない\]**  
 このドキュメントで既に説明した **\[警告の構成\]** テーブルでの指定に従って、コンパイラに通知の発行を許可するかどうかを指定します。  既定では、このチェック ボックスはオフになっています。  コンパイラに警告やエラーを発行しないよう指示する場合は、このチェック ボックスをオンにします。  
  
 この設定は、[\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) コンパイラ オプションに対応します。  
  
 **\[すべての警告をエラーとして扱う\]**  
 警告の処理方法を指定します。  このチェック ボックスは、既定でオフになります。この場合、すべての警告通知が **\[警告\]** に設定されたままになります。  すべての警告通知を **\[エラー\]** に変更する場合は、このチェック ボックスをオンにします。  
  
 このオプションは、**\[すべての警告を表示しない\]** がオフの場合にのみ使用できます。  
  
 **\[XML ドキュメント ファイルを生成する\]**  
 ドキュメント情報を生成するかどうかを指定します。  既定では、このチェック ボックスはオンになり、ドキュメント情報を生成して XML ファイルに含めるようにコンパイラに指示します。  ドキュメントを作成しないようにコンパイラに指示するには、このチェック ボックスをオフにします。  
  
 この設定は、[\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) コンパイラ オプションに対応します。  
  
 **\[COM の相互運用機能に登録\]**  
 マネージ アプリケーションで COM オブジェクト \(COM 呼び出し可能ラッパー\) を公開し、COM オブジェクトがアプリケーションとやり取りできるようにするかどうかを指定します。  
  
 既定では、このチェック ボックスはオフになります。この場合、アプリケーションは COM 相互運用機能を無効にします。  COM 相互運用機能を有効にする場合は、このチェック ボックスをオンにします。  
  
 このオプションは、Windows アプリケーション プロジェクトやコンソール アプリケーション プロジェクトでは指定できません。  
  
 **\[ビルド イベント\]**  
 **\[ビルド イベント\]** ダイアログ ボックスにアクセスするには、このボタンをクリックします。  このダイアログ ボックスは、プロジェクトに対するビルド前の構成命令およびビルド後の構成命令を指定するために使用します。  このダイアログ ボックスは、Visual Basic プロジェクトでのみ使用できます。  詳細については、「[\[ビルド イベント\] ダイアログ ボックス \(Visual Basic\)](../Topic/Build%20Events%20Dialog%20Box%20\(Visual%20Basic\).md)」を参照してください。  
  
 **\[詳細コンパイル オプション\]**  
 **\[コンパイラの詳細設定\]** ダイアログ ボックスにアクセスするには、このボタンをクリックします。  **\[コンパイラの詳細設定\]** ダイアログ ボックスは、プロジェクトの詳細ビルド構成プロパティを指定するために使用します。  このダイアログ ボックスは、Visual Basic プロジェクトでのみ使用できます。  詳細については、「[\[ビルドの詳細設定\] ダイアログ ボックス \(Visual Basic\)](../Topic/Advanced%20Compiler%20Settings%20Dialog%20Box%20\(Visual%20Basic\).md)」を参照してください。  
  
## 参照  
 [Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)   
 [Managing Compilation Properties](http://msdn.microsoft.com/ja-jp/94308881-f10f-4caf-a729-f1028e596a2c)   
 [方法 : ビルド イベントを指定する \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [方法 : 構成を作成および編集する](../../ide/how-to-create-and-edit-configurations.md)