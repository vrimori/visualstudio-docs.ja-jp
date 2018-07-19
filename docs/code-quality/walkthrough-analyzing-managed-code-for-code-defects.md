---
title: コードをマネージ コードの欠陥のチュートリアルの分析 |Microsoft Docs
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 49c122e5cf22e9290f6dab1d45539887c68c01bd
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117720"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>チュートリアル: コードの分析のマネージ コードを欠陥します。

このチュートリアルでは、コード分析ツールを使用してマネージ プロジェクトのコードの不具合を分析します。

このチュートリアルでは、コード分析を使用して、Microsoft .NET Framework デザイン ガイドラインに準拠するため、.NET マネージ コード アセンブリを分析するプロセスを手順します。

## <a name="create-a-class-library"></a>クラス ライブラリを作成します。

### <a name="to-create-a-class-library"></a>クラス ライブラリを作成するには

1. **[ファイル]** メニューで、**[新規]** > **[プロジェクト]** の順に選択します。

1. **新しいプロジェクト** ダイアログ ボックスで、展開**インストール済み** > **Visual c#** を選び、 **Windows デスクトップ**します。

1. 選択、**クラス ライブラリ (.NET Framework)** テンプレート。

1. **名前**テキスト ボックスに「 **CodeAnalysisManagedDemo**順にクリックします**OK**します。

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

1. プロジェクトを CodeAnalysisManagedDemo 選択**ソリューション エクスプ ローラー**します。

1. **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

     CodeAnalysisManagedDemo プロパティ ページが表示されます。

1. 選択、**コード分析**タブ。

1. 必ず**ビルドに対するコード分析を有効にする**がチェックされます。

1. **この規則セットを実行**ドロップダウン リストで、 **Microsoft のすべてのルール**します。

1. **ファイル** メニューのをクリックして**選択した項目の保存**、プロパティ ページを閉じます。

1. **ビルド** メニューのをクリックして**ビルド CodeAnalysisManagedDemo**します。

    CodeAnalysisManagedDemo プロジェクトのビルド警告が表示されます、**エラー一覧**と**出力**windows。

## <a name="correct-the-code-analysis-issues"></a>コード分析の問題を修正します。

### <a name="to-correct-code-analysis-rule-violations"></a>コード分析規則違反を修正するには

1. **ビュー** ] メニューの [選択**エラー一覧**します。

    選択した開発者のプロファイルによってをポイントする必要があります**その他の Windows**で、**ビュー** ] メニューの [選び、**エラー一覧**。

1. **ソリューション エクスプ ローラー**、選択**すべてのファイル**します。

1. [プロパティ] ノードを展開し、開きます、 *AssemblyInfo.cs*ファイル。

1. 警告を修正するのに、次のヒントを使用します。

   [Ca 1014: アセンブリに CLSCompliantAttribute をマークする](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'demo' は、CLSCompliantAttribute でマークする必要があり、その値を true にする必要があります。

   1. コードを追加`using System;`AssemblyInfo.cs ファイルにします。

   1. 次に、コードを追加`[assembly: CLSCompliant(true)]`AssemblyInfo.cs ファイルの末尾にします。

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo(String)。

   1. コンス トラクターを追加`public demo (String s) : base(s) { }`クラスに`demo`します。

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリックのデモ (String, 例外)。

   1. コンス トラクターを追加`public demo (String s, Exception e) : base(s, e) { }`クラスに`demo`します。

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますデモ (SerializationInfo, StreamingContext) を保護。

   1. コードを追加`using System.Runtime.Serialization;`Class1.cs ファイルの先頭にします。

   1. 次に、コンス トラクターを追加します。 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo()。

   1. コンス トラクターを追加`public demo () : base() { }`クラスに`demo`**します。**

   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'TestCode' に変更することによって空間' プログラム名' の大文字と小文字を修正します。

   1. 名前空間の大文字と小文字を変更する`testCode`に`TestCode`します。

   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming:"Demo"に変更することによって、型名 'demo' の大文字と小文字を修正します。

   1. メンバーの名前を変更`Demo`します。

   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Item' に変更することによって、メンバー名 'item' の大文字と小文字を修正します。

   1. メンバーの名前を変更`Item`します。

   [1710: 識別子は正しいサフィックスをいなければなりません](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: 名前の変更 'testCode.demo' を 'Exception' で終了します。

   1. クラスとそのコンス トラクターの名前を変更`DemoException`します。

   [Ca 2210: アセンブリが有効な厳密な名前](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'CodeAnalysisManagedDemo' を厳密な名前のキーで署名します。

   1. **プロジェクト**] メニューの [選択**CodeAnalysisManagedDemo プロパティ**します。

      プロジェクトのプロパティが表示されます。

   1. **[署名]** タブを選択します。

   1. 選択、**アセンブリに署名**チェック ボックスをオンします。

   1. **厳密な名前キー ファイルを選択**一覧で、[ **\<新規作成] >** します。

      **厳密な名前キーの作成** ダイアログ ボックスが表示されます。

   1. **キー ファイル名**TestKey を入力します。

   1. パスワードを入力し、 **OK**します。

   1. **ファイル**] メニューの [選択**選択した項目の保存**、プロパティ ページを閉じます。

   [Ca 2237: ISerializable 型を SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: この型が ISerializable を実装している 'デモ' を入力する [Serializable] 属性を追加します。

   1. 追加、`[Serializable ()]`属性をクラス`demo`します。

   変更を完了した後、次のよう Class1.cs ファイルになります。

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

    1. 警告を選択して、**エラー一覧**します。

    1. 右クリックまたはコンテキスト メニューから選択**抑制** > **抑制ファイル内**します。

1. プロジェクトをリビルドします。

     プロジェクトは、警告やエラーなしでビルドします。

## <a name="see-also"></a>関連項目

[マネージ コードのコード分析](../code-quality/code-analysis-for-managed-code-overview.md)