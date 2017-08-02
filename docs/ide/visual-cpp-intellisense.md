---
title: "Visual C++ の Intellisense | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 555a0f9b39d28166c0f414b1bcbf81c2a137d0ff
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---
# <a name="visual-c-intellisense"></a>Visual C# の IntelliSense
Visual Studio 2015 では、単一コードのファイルおよびプロジェクト内のファイルに対して IntelliSense を利用できます。 クロスプラット フォーム プロジェクトでは、いくつかの IntelliSense 機能が、Android や iOS のコンテキスト内にいるときでも共有コード プロジェクト内の .cpp および .c ファイルで使用できます。  
  
## <a name="intellisense-features-in-c"></a>C++ の IntelliSense 機能  
 IntelliSense は、コード作成をより便利にするための一連の機能に与えられた名前です。 便利さについては、人によって考え方が違うので、ほぼすべての IntelliSense 機能を **[テキスト エディター]、[C/C++]、[詳細]** プロパティ ページで有効または無効にできます。  
  
 ![[ツール]、[オプション]、[テキスト エディター]、[C&#47;C&#43;&#43;]、[詳細]](~/docs/ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")  
  
 次の画像のメニュー項目とキーボード ショートカットを使用すると、IntelliSense にアクセスできます。  
  
 ![Visual C&#43;&#43; の [IntelliSense] メニュー](~/docs/ide/media/vs2015_cpp_intellisense_menu.png "vs2015_cpp_intellisense_menu")  
  
### <a name="statement-completion-and-member-list"></a>ステートメント入力候補およびメンバーの一覧  
 キーワード、型、関数、変数名、またはコンパイラが認識するその他のプログラム要素の入力を開始すると、エディターがワードの入力候補を提供します。  
  
 アイコンとその意味の一覧は、「[[クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン](../ide/class-view-and-object-browser-icons.md)」を参照してください。  
  
 ![Visual C&#43;&#43; の [入力候補] ウィンドウ](~/docs/ide/media/vs2015_cpp_complete_word.png "vs2015_cpp_complete_word")  
  
 メンバーの一覧を最初に起動するときに、現在のコンテキストにアクセス可能であるメンバーだけが表示されます。 その後 **Ctrl + J** を使用すると、アクセス可能かどうかにかかわらず、すべてのメンバーが表示されます。 3 回目に実行すると、プログラム要素のより多くの一覧が表示されます。 **C/C++ の全般オプション** ページで入力候補をオフにすることができます。  
  
 ![Visual C&#43;&#43; メンバーの一覧](~/docs/ide/media/vs2015_cpp_list_members.png "vs2015_cpp_list_members")  
  
### <a name="parameter-help"></a>パラメーターのヘルプ  
 関数呼び出しで左中かっこを入力するか、クラス テンプレートの変数宣言で山かっこを入力すると、エディターは関数またはコンストラクターの各オーバーロードのパラメーターの型を含む小さいウィンドウを表示します。 カーソルの場所に基づく「現在」のパラメーターは、太字で表示します。 **C/C++ の全般オプション** ページで入力候補をオフにすることができます。  
  
 ![Visual C&#43;&#43; のパラメーターのヘルプ](~/docs/ide/media/vs_2015_cpp_param_help.png "vs_2015_cpp_param_help")  
  
### <a name="quick-info"></a>クイック ヒント  
 変数の上にマウス カーソルを移動すると、小さなウィンドウがインラインで表示され、型の情報と型が定義されているヘッダーが表示されます。 関数のシグネチャを表示するには、関数呼び出しの上にカーソルを置きます。 **[テキスト エディター]、[C/C++]、[詳細]** ページで、クイック ヒントをオフにすることができます。  
  
 ![Visual C&#43;&#43; のクイックヒント](~/docs/ide/media/vs2015_cpp_quickinfo.png "vs2015_cpp_quickInfo")  
  
## <a name="error-squiggles"></a>エラーの波線  
 プログラム要素 (変数、キーワード、中かっこ、型名など) の下の波線は、コード内のエラーや潜在的なエラーに注意を引くためのものです。 まだ実装を記述する必要があることを通知するために、事前宣言を記述するときに、緑の波線が表示されます。 Windows のコンテキストで作業しているものの、Android のコンテキストではエラーになる内容を入力するなど、現在アクティブでないコードにエラーがある場合、共有プロジェクトに紫の波線が表示されます。 赤の波線は、コンパイラ エラーまたは警告が現在のコードにあり、対処する必要があることを示します。  
  
 ![Visual C&#43;&#43; のエラーの波線](~/docs/ide/media/vs2015_cpp_error_quiggles.png "vs2015_cpp_error_quiggles")  
  
## <a name="code-colorization-and-fonts"></a>コードの色付けとフォント  
 既定の色とフォントは、**[環境]、[フォントおよび色]** プロパティ ページで変更することができます。 ここでは、エディターだけでなく、多数の UI ウィンドウのフォントを変更することができます。 C++ に固有の設定は "C++" で始まり、その他の設定はすべての言語で利用できます。  
  
## <a name="cross-platform-intellisense"></a>クロス プラットフォームの IntelliSense  
 共有コード プロジェクトでは、Android のコンテキストを使用している場合でも、波線などのいくつかの IntelliSense 機能を使用できます。 非アクティブなプロジェクトでエラーになるいくつかのコードを記述すると、IntelliSense が波線を表示しますが、現在のコンテキストでのエラーの波線とは色が異なります。  
  
 ここでは、Android や iOS 用にビルドするように構成されている OpenGLES アプリケーションを示します。 この図は編集中の共有コードを示します。 最初の図では、Android がアクティブなプロジェクトです。  
  
 ![Android プロジェクトはアクティブなプロジェクトです。](~/docs/ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")  
  
 次の点に注意してください。  
  
-   __ANDROID\_\_ が Android プロジェクトに対して定義されているため、8 行目の #else 分岐は淡色表示で非アクティブ領域として表示されています。  
  
-   11 行目のあいさつの変数は HELLO 識別子で初期化され、紫の波線で表示されています。 これは現在アクティブではない iOS プロジェクトに、HELLO 識別子が定義されていないためです。 Android プロジェクトでは、11 行目がコンパイルされますが、iOS ではコンパイルされません。 これは共有コードのため、現在アクティブな構成でコンパイルする場合でも、変更する必要があります。  
  
-   12 行目の BYE 識別子は赤の波線で表示されており、現在選択されているアクティブ プロジェクトでは定義されていません。  
  
 ここで、アクティブなプロジェクトを iOS.StaticLibrary に変更し、波線がどう変化するかに注目してください。  
  
 ![アクティブなプロジェクトとして iOS が選択されています。](~/docs/ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")  
  
 次の点に注意してください。  
  
-   __ANDROID\_\_ が iOS プロジェクトに対して定義されていないため、6 行目の #ifdef 分岐は淡色表示で非アクティブ領域として表示されています。  
  
-   11 行目のあいさつの変数は、HELLO 識別子で初期化され、赤の波線で表示されています。 これは現在アクティブな iOS プロジェクトに、HELLO 識別子が定義されていないためです。  
  
-   12 行目の BYE 識別子は紫の波線で表示されており、現在非アクティブな Android.NativeActivity プロジェクトでは定義されていません。  
  
## <a name="single-file-intellisense"></a>単一ファイルの IntelliSense  
 プロジェクトの外部で 1 つのファイルを開いても、やはり IntelliSense を取得します。 **[テキスト エディター]、[C/C++]、[詳細]** にアクセスして IntelliSense 機能をオン/オフすることにより、特定の機能を有効または無効にすることができます。 プロジェクトの一部ではない 1 つのファイルに IntelliSense を構成するには、**[詳細設定]** のセクションで **IntelliSense and Browsing for Non-Project Files** (IntelliSense およびプロジェクト以外のファイルの参照) を検索します。 「[Visual C++ ガイド ツアー](http://msdn.microsoft.com/en-us/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)」を参照してください。  
  
 ![Visual C&#43;&#43; の単一ファイルの IntelliSense](~/docs/ide/media/vs2015_cpp_single_file_intellisense.png "vs2015_cpp_single_file_intellisense")  
  
 既定では、単一ファイルの IntelliSense は標準のインクルード ディレクトリだけを使用してヘッダー ファイルを検索します。 他にディレクトリを追加するには、次の図に示すとおり、ソリューション ノードのショートカット メニューを開き、**[デバッグ ソース ファイル]** リストにディレクトリを追加します。  
  
 ![ヘッダー ファイルまでのパスを追加しています。](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")  
  
## <a name="see-also"></a>関連項目  
 [IntelliSense の使用](../ide/using-intellisense.md)
