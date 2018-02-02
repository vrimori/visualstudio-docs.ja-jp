---
title: "コードの不具合のマネージ コードのチュートリアルの分析 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: e1c708f31d31dd811017015cd37c7e60d49beef9
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>チュートリアル: コードの分析のマネージ コードを欠陥します。

このチュートリアルでコード分析ツールを使用してマネージ プロジェクトのコードの不具合を分析します。

このチュートリアルは、Microsoft .NET Framework デザイン ガイドラインに準拠するため、.NET マネージ コード アセンブリを分析するコード分析を使用して処理する手順を示します。

## <a name="create-a-class-library"></a>クラス ライブラリを作成します。

### <a name="to-create-a-class-library"></a>クラス ライブラリを作成するには

1. **ファイル**] メニューの [選択**新規** > **プロジェクト.**.

1. **新しいプロジェクト** ダイアログ ボックスで、展開**インストール** > **Visual c#**を選択し**Windows クラシック デスクトップ**です。

1. 選択、**クラス ライブラリ (.NET Framework)**テンプレート。

1. **名前**テキスト ボックスで、「 **CodeAnalysisManagedDemo**順にクリック**OK**です。

1. プロジェクトを作成すると後で開く、 *Class1.cs*ファイル。

1. Class1.cs の既存のテキストを次のコードに置き換えます。

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Class1.cs ファイルを保存します。

## <a name="analyze-the-project"></a>プロジェクトを分析します。

### <a name="to-analyze-a-managed-project-for-code-defects"></a>マネージ プロジェクトのコードの不具合を分析するには

1. CodeAnalysisManagedDemo プロジェクトを選択**ソリューション エクスプ ローラー**です。
  
1. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。
  
     CodeAnalysisManagedDemo プロパティ ページが表示されます。
  
1. 選択、**コード分析**タブです。
  
1. 確認して**ビルドに対するコード分析を有効にする**がオンになっています。
  
1. **この規則セットを実行**ドロップダウン リストで、 **Microsoft すべてルール**です。
  
1. **ファイル** メニューのをクリックして**選択した項目の保存**、プロパティ ページを閉じます。
  
1. **ビルド** メニューのをクリックして**ビルド CodeAnalysisManagedDemo**です。
  
    CodeAnalysisManagedDemo プロジェクトのビルド警告が表示されます、**エラー一覧**と**出力**windows です。

## <a name="correct-the-code-analysis-issues"></a>コード分析の問題を修正します。

### <a name="to-correct-code-analysis-rule-violations"></a>コード分析規則違反を修正

1. **ビュー** ] メニューの [選択**エラー一覧**です。

    によっては、選択した開発者プロファイルを指す必要があります**その他のウィンドウ**上、**ビュー**  メニューを選択し**エラー一覧**です。

1. **ソリューション エクスプ ローラー**、選択**すべてのファイル**です。

1. [プロパティ] ノードを展開し、開きます、 *AssemblyInfo.cs*ファイル。

1. 警告を解決するのには、以下のヒントを使用します。

   [Ca 1014: アセンブリに CLSCompliantAttribute をマークする](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design:"demo"、CLSCompliantAttribute とマークし、その値を true にする必要があります。

   1. コードを追加`using System;`AssemblyInfo.cs ファイルにします。

   1. 次に、コードを追加`[assembly: CLSCompliant(true)]`AssemblyInfo.cs ファイルの末尾にします。

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo(String)。

   1. コンス トラクターを追加`public demo (String s) : base(s) { }`クラスに`demo`です。

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリックのデモ (String, 例外)。

   1. コンス トラクターを追加`public demo (String s, Exception e) : base(s, e) { }`クラスに`demo`です。

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますデモ (SerializationInfo、StreamingContext) を保護。

   1. コードを追加`using System.Runtime.Serialization;`Class1.cs ファイルの先頭にします。

   1. 次に、コンス トラクターを追加します。`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo()。

   1. コンス トラクターを追加`public demo () : base() { }`クラスに`demo`**です。**

   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'TestCode' に変更することによって、空間' プログラム名' の大文字と小文字を解決します。

   1. 名前空間の大文字と小文字を変更する`testCode`に`TestCode`です。

   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming:"Demo"に変更すると、型名"demo"の大文字と小文字を修正します。

   1. メンバーの名前を変更`Demo`です。

   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Item' に変更すると、メンバー名 'item' の大文字と小文字を修正します。

   1. メンバーの名前を変更`Item`です。

   [1710: 識別子は正しいサフィックスをいなければなりません](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: 名前を変更する 'testCode.demo' を 'Exception' で終了します。

   1. クラスとそのコンス トラクターの名前を変更`DemoException`です。

   [Ca 2210: アセンブリは有効な厳密な名前である必要があります](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'CodeAnalysisManagedDemo' を厳密な名前のキーで署名します。

   1. **プロジェクト**] メニューの [選択**CodeAnalysisManagedDemo プロパティ**です。

      プロジェクトのプロパティが表示されます。

   1. **[署名]** タブを選択します。

   1. 選択、**アセンブリに署名**チェック ボックスをオンします。

   1. **厳密な名前キー ファイルを選択**一覧で、 **\<新規… >**です。

      **厳密な名前キーの作成** ダイアログ ボックスが表示されます。

   1. **キー ファイル名**TestKey を入力します。

   1. パスワードを入力し、 **OK**です。

   1. **ファイル**] メニューの [選択**選択した項目の保存**、プロパティ ページを閉じます。

   [Ca 2237: ISerializable 型を SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: この型が ISerializable を実装する、その 'デモ' を入力する [Serializable] 属性を追加します。

   1. 追加、`[Serializable ()]`属性クラスを`demo`です。

   変更を完了すると、Class1.cs ファイルは、次のようになります。

   ```csharp
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

1. プロジェクトをリビルドします。

## <a name="exclude-code-analysis-warnings"></a>コード分析の警告を除外します。

### <a name="to-exclude-code-defect-warnings"></a>コード障害の警告を除外するには

1. 残りの警告のそれぞれについて、次の操作を行います。

    1. 警告を選択して、**エラー一覧**です。

    1. 右クリックまたはコンテキスト メニューから選択**抑制** > **抑制ファイル内**です。

1. プロジェクトをリビルドします。

     警告またはエラーを行わなくても、プロジェクトをビルドします。

## <a name="see-also"></a>関連項目

[マネージ コードのコード分析](../code-quality/code-analysis-for-managed-code-overview.md)