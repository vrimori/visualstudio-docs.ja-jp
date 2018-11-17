---
title: C++ Core ガイドライン チェッカーの使用 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1153f7a32c26946fafb1230699c4afcae976cd9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799562"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Core ガイドライン チェッカーの使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core ガイドラインは、ガイドライン、ルール、および C++ 専門家とデザイナーで作成された C++ のコーディングについてのベスト プラクティスの移植可能なセットです。  Visual Studio では、アドインのパッケージを分析ツールへの準拠、C++ Core Guidelines のコードを確認し、改善点を提案するコードの追加の規則を作成できるようになりました。  
  
## <a name="the-c-core-guidelines-project"></a>C++ Core ガイドラインのプロジェクト  
 Bjarne Stroustrup と他のユーザーによって作成された、C++ Core Guidelines は、安全で効果的に最新の C++ を使用するためのガイドです。 ガイドラインは、静的な型の安全性とリソースの安全性を強調します。 排除または言語のエラーを起こしやすい部分を最小化する方法を特定され、信頼性の高い方法でパフォーマンスが向上と、コードを簡素化する方法をお勧めします。 次のガイドラインは、標準の C++ Foundation によって管理されます。 詳細については、ドキュメントを参照してください。 [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)、C++ Core Guidelines のドキュメントのプロジェクト ファイルにアクセスして[GitHub](https://github.com/isocpp/CppCoreGuidelines)します。  
  
 Microsoft では、C++ Core Check コード分析規則セットを Nuget パッケージを使用して、プロジェクトに追加できることで、C++ Core Guidelines の作業をサポートしています。 パッケージの名前は Microsoft.CppCoreCheck とで使用可能になる[ http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck)します。 このパッケージには少なくとも Visual Studio 2015 Update 1 でインストールが必要になります。  
  
 パッケージには、依存関係をヘッダーのみのガイドライン サポート ライブラリ (GSL) として別のパッケージもインストールされます。 GitHub の「使用可能な、GSL も[ https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)します。  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>C++ Core Check のガイドラインにコード分析を有効にします。  
 C++ Core Check のコード分析ツールを有効にするには、Visual Studio 内で確認したい各の C++ プロジェクトに Microsoft.CppCoreCheck NuGet パッケージをインストールします。  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Microsoft.CppCoreCheck パッケージをプロジェクトに追加するには  
  
1. **ソリューション エクスプ ローラー**、右クリックすると、パッケージを追加するソリューションで、プロジェクトのコンテキスト メニューを開きます。 選択**NuGet パッケージの管理**を開く、 **NuGet パッケージ マネージャー**します。  
  
2. **NuGet パッケージ マネージャー**ウィンドウで、Microsoft.CppCoreCheck を検索します。  
  
    ![Nuget パッケージ マネージャー ウィンドウは、CppCoreCheck パッケージを示しています](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window。")  
  
3. Microsoft.CppCoreCheck パッケージを選択し、選択、**インストール**をプロジェクトに規則を追加するボタンをクリックします。  
  
   NuGet パッケージでは、プロジェクトでコード分析を有効にしたときに呼び出されるプロジェクトに追加の MSBuild .targets ファイルを追加します。 この .targets ファイルでは、Visual Studio コード分析ツールに追加の拡張機能として、C++ Core Check の規則を追加します。  
  
   選択してプロジェクトでコード分析を有効にすることができます、**ビルドに対するコード分析を有効にする**でチェック ボックスをオン、**コード分析**のセクション、**プロパティ ページ**のダイアログ ボックスプロジェクト。  
  
   ![コード分析の全般設定のプロパティ ページ](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Core Check の規則では、コード分析が有効になっているときに実行される既定の規則セットの一部になります。 C++ Core Check の規則では、開発中であるため、いくつかのルールは、すべてのコードで使用する準備ができていない可能性がありますが、開発中に有益あります。 これらの規則は、実験用にリリースされます。 プロジェクトのプロパティでリリースされたまたは試験用の規則を実行するかどうかを選択できます。  
  
   ![コード分析の拡張機能設定のプロパティ ページ](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   有効または、C++ Core Check の規則セットを無効にする、開く、**プロパティ ページ**プロジェクトのダイアログ。 **構成プロパティ**、展開**コード分析**、**拡張**します。 横にドロップダウン リストで制御**を有効にする C++ Core の Check (リリース)** または**を有効にする C++ Core の Check (試験段階)**、選択**はい**または**いいえ**します。 選択**OK**または**適用**変更を保存します。  
  
## <a name="check-types-bounds-and-lifetimes"></a>型、境界、および有効期間を確認してください。  
 C++ Core Check パッケージには、現在のチェッカーが含まれる、[タイプ セーフ](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type)、[安全性の境界](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)、および[有効期間の安全性](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime)プロファイル。  
  
 C++ Core Check の規則を検索する問題の種類の例を次に示します。  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 この例では、C++ Core Check の規則を検索する警告のいくつかを示します。  
  
- C26494 はルール Type.5: 常にオブジェクトを初期化します。  
  
- C26485 はルール Bounds.3: 配列からポインターへの減退しません。  
  
- C26481 はルール Bounds.1: ポインター演算を使用しないでください。 代わりに、`span` を使用してください。  
  
  C++ Core Check のコード分析ルールセットはインストールされている、このコードをコンパイルすると、最初の 2 つの警告は、出力が、3 つ目の抑制を有効になっている場合。 コード例からのビルド出力を次に示します。  
  
  **1 >---ビルド開始: プロジェクト: CoreCheckExample、構成: デバッグ Win32--**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj C:\Users\username\documents\visual studio 2015\P を ->**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj C:\Users\username\documents\visual studio 2015\P を ->**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (完全な PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): C26494 の警告: 変数 'arr' は uninitializ**  
**編集上は、常にオブジェクトを初期化します。(type.5: http://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): 警告 C26485: 式 'arr': 配列からなし**  
 **ポインターへの減退します。(bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**ステージのビルド: 1 正常終了、解像度 0 の失敗、0 が最新の状態、0 スキップ ステージ**より、安全なコードを記述するために、C++ Core ガイドラインはあります。 ただし、場所、ルール、またはプロファイルを適用しないインスタンスがある場合を簡単に、コード内で直接非表示になります。 使用することができます、`gsl::suppress`を検出して、次のコード ブロックの規則の違反をレポートから C++ Core Check を保持する属性。 特定のルールを抑制する個々 のステートメントをマークすることができます。 記述することで、全体の bounds プロファイルを抑制することができますも`[[gsl::suppress(bounds)]]`含めず、特定のルールの数。  
  
## <a name="use-the-guideline-support-library"></a>ガイドライン サポート ライブラリを使用します。  
 Microsoft.CppCoreCheck NuGet パッケージには、Microsoft の実装のガイドライン サポート ライブラリ (GSL) を含むパッケージもインストールされます。 あるスタンドアロンのフォームで使用できる、GSL も[ http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl)します。 このライブラリは、コアのガイドラインに従う場合に便利です。 GSL より安全な代替手段でエラーが発生しやすい構成要素を置き換えますできる定義が含まれます。 などに置き換えることができます、`T*, length`パラメーターのペア、`span<T>`型。 ライブラリのソースがコメントの追加、またはドキュメントに投稿を見てしたい場合は、GSL、オープン ソースのプロジェクトにある[ https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)します。



