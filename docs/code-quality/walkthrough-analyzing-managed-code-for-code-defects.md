---
title: "チュートリアル: マネージ コードを分析するコードの不具合の |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3dd0c93476e646895362b98c2f62b569d87ffe35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>チュートリアル: マネージ コードの分析によるコード障害の検出
このチュートリアルでは、コード分析ツールを使用して、マネージ プロジェクトのコードの不具合を分析します。  
  
 このチュートリアルのステップのコード分析を使用して、.NET マネージ コード アセンブリは、Microsoft .NET Framework デザイン ガイドラインへの適合性を分析するプロセス。  
  
 このチュートリアルでしました。  
  
-   分析し、コード障害の警告を修正します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]。  
  
## <a name="create-a-class-library"></a>クラス ライブラリを作成します。  
  
#### <a name="to-create-a-class-library"></a>クラス ライブラリを作成するには  
  
1.  **ファイル**のメニュー [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]、 をクリックして**新規** をクリックし、**プロジェクト**です。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類**をクリックして**Visual c#**です。  
  
3.  **テンプレート****クラス ライブラリ**です。  
  
4.  **名前**テキスト ボックスで、「 **CodeAnalysisManagedDemo**順にクリック**OK**です。  
  
5.  プロジェクトを作成すると、後に、Class1.cs ファイルを開きます。  
  
6.  Class1.cs の既存のテキストを次のコードに置き換えます。  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Class1.cs ファイルを保存します。  
  
## <a name="analyze-the-project"></a>プロジェクトを分析します。  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>マネージ プロジェクトのコードの不具合を分析するには  
  
1.  CodeAnalysisManagedDemo プロジェクトを選択**ソリューション エクスプ ローラー**です。  
  
2.  **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
     CodeAnalysisManagedDemo プロパティ ページが表示されます。  
  
3.  をクリックして**CodeAnalysis**です。  
  
4.  確認して**ビルドに対するコード分析を有効にする (定数 CODE_ANALYSIS を定義**) がオンになっています。  
  
5.  **この規則セットを実行**ドロップダウン リストで、 **Microsoft すべてルール**です。  
  
6.  **ファイル** メニューのをクリックして**選択した項目の保存**ManagedDemo のプロパティ ページを閉じます。  
  
7.  **ビルド** メニューのをクリックして**ビルド ManagedDemo**です。  
  
     CodeAnalysisManagedDemo プロジェクトのビルド警告が報告される、**コード分析**と**出力**windows です。  
  
     場合、**コード分析**ウィンドウが表示されないに、**分析**] メニューの [選択**Windows**し**コード分析を選択**です。  
  
## <a name="correct-the-code-analysis-issues"></a>コード分析の問題を修正します。  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>コード分析規則違反を修正  
  
1.  **ビュー**  メニューのをクリックして**エラー一覧**です。  
  
     選択した開発者プロファイルに応じてを指す必要があります**その他のウィンドウ**で、**ビュー**  メニューをクリックして**エラー一覧**です。  
  
2.  **ソリューション エクスプ ローラー**をクリックして**すべてのファイル**です。  
  
3.  次に、[プロパティ] ノードを展開し、AssemblyInfo.cs ファイルを開きます。  
  
4.  警告を解決するのにには、次を使用します。  
  
-   [Ca 1014: アセンブリに CLSCompliantAttribute をマークする](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design:"demo"、CLSCompliantAttribute とマークし、その値を true にする必要があります。  
  
    -   コードを追加`using``System;`AssemblyInfo.cs ファイルにします。  
  
         次に、コードを追加`[assembly: CLSCompliant(true)]`AssemblyInfo.cs ファイルの末尾にします。  
  
         プロジェクトをリビルドします。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo(String)。  
  
    -   コンス トラクターを追加`public demo (String s) : base(s) { }`クラスに`demo`です。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリックのデモ (String, 例外)。  
  
    -   コンス トラクターを追加`public demo (String s, Exception e) : base(s, e) { }`クラスに`demo`です。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますデモ (SerializationInfo、StreamingContext) を保護。  
  
    -   コードを追加`using System.Runtime.Serialization;`Class1.cs ファイルの先頭にします。  
  
         次に、コンス トラクターを追加します。`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         プロジェクトをリビルドします。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo()。  
  
    -   コンス トラクターを追加`public demo () : base() { }`クラスに`demo`**です。**  
  
         プロジェクトをリビルドします。  
  
-   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'TestCode' に変更することによって、空間' プログラム名' の大文字と小文字を解決します。  
  
    -   名前空間の大文字と小文字を変更する`testCode`に`TestCode`です。  
  
-   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming:"Demo"に変更すると、型名"demo"の大文字と小文字を修正します。  
  
    -   メンバーの名前を変更`Demo`です。  
  
-   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Item' に変更すると、メンバー名 'item' の大文字と小文字を修正します。  
  
    -   メンバーの名前を変更`Item`です。  
  
-   [1710: 識別子は正しいサフィックスをいなければなりません](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: 名前を変更する 'testCode.demo' を 'Exception' で終了します。  
  
    -   クラスとそのコンス トラクターの名前を変更`DemoException`です。  
  
-   [Ca 2210: アセンブリは有効な厳密な名前である必要があります](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'ManagedDemo' を厳密な名前のキーで署名します。  
  
    -   **プロジェクト** メニューのをクリックして**ManagedDemo プロパティ**です。  
  
         プロジェクトのプロパティが表示されます。  
  
         をクリックして**署名**です。  
  
         選択、**アセンブリに署名**チェック ボックスをオンします。  
  
         **厳密な名前キー ファイルを選択**一覧で、 **\<新規… >**です。  
  
         **厳密な名前キーの作成** ダイアログ ボックスが表示されます。  
  
         **キー ファイル名**TestKey を入力します。  
  
         パスワードを入力し、クリックして**OK**です。  
  
         **ファイル** メニューのをクリックして**選択した項目の保存**、プロパティ ページを閉じます。  
  
         プロジェクトをリビルドします。  
  
-   [Ca 2237: ISerializable 型を SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: この型が ISerializable を実装する、その 'デモ' を入力する [Serializable] 属性を追加します。  
  
    -   追加、`[Serializable ()]`属性クラスを`demo`です。  
  
         プロジェクトをリビルドします。  
  
 変更を完了すると、Class1.cs ファイルは、次のようになります。  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
using System;  
using System.Runtime.Serialization;  
  
namespace TestCode  
{  
  
    [Serializable()]   
    public class DemoException : Exception  
    {  
        public DemoException () : base() { }  
        public DemoException(String s) : base(s) { }  
        public DemoException(String s, Exception e) : base(s, e) { }  
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }  
  
        public static void Initialize(int size) { }  
        protected static readonly int _item;  
        public static int Item { get { return _item; } }  
    }  
}  
```  
  
## <a name="exclude-code-analysis-warnings"></a>コード分析の警告を除外します。  
  
#### <a name="to-exclude-code-defect-warnings"></a>コード障害の警告を除外するには  
  
1.  残りの警告のそれぞれについて、次の操作を行います。  
  
    1.  コード分析 ウィンドウで、警告を選択します。  
  
    2.  選択**アクション**、順に選択**メッセージの非表示**を選択し**プロジェクト抑制ファイル内**です。  
  
     詳細については、次を参照してください[する方法: メニュー項目を使用して警告を抑制する状況。](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  プロジェクトをリビルドします。  
  
     警告またはエラーを行わなくても、プロジェクトをビルドします。