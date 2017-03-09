---
title: "チュートリアル: マネージ コードの分析によるコード障害の検出 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード分析、チュートリアル"
  - "マネージ コード、分析"
  - "コード分析ツール、チュートリアル"
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 45
caps.handback.revision: 45
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# チュートリアル: マネージ コードの分析によるコード障害の検出
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、コード分析ツールを使用して、マネージ プロジェクトのコードの不具合を分析します。  
  
 このチュートリアルでは、コード分析を使用して、Microsoft .NET Framework デザイン ガイドラインに準拠するため、.NET マネージ コード アセンブリを分析するプロセスを手順です。  
  
 このチュートリアルでしました。  
  
-   分析し、コード障害の警告を修正します。  
  
## <a name="prerequisites"></a>必要条件  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]。  
  
## <a name="create-a-class-library"></a>クラス ライブラリを作成します。  
  
#### <a name="to-create-a-class-library"></a>クラス ライブラリを作成するには  
  
1.   **ファイル** ] メニューの [ [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], 、] をクリックして **新規** ] をクリックし、 **プロジェクト**します。  
  
2.   **新しいプロジェクト** ダイアログ ボックスで、 **プロジェクトの種類**, をクリックして **Visual c#**します。  
  
3.   **テンプレート**, [ **クラス ライブラリ**します。  
  
4.   **名前** テキスト ボックスに「 **CodeAnalysisManagedDemo** ] をクリックし、 **OK**します。  
  
5.  プロジェクトを作成した後は、Class1.cs ファイルを開きます。  
  
6.  Class1.cs の既存のテキストを次のコードに置き換えます。  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Class1.cs ファイルを保存します。  
  
## <a name="analyze-the-project"></a>プロジェクトを分析します。  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>マネージ プロジェクトのコードの不具合を分析するには  
  
1.  CodeAnalysisManagedDemo プロジェクトを選択 **ソリューション エクスプ ローラー**します。  
  
2.   **プロジェクト** ] メニューのをクリックして **プロパティ**します。  
  
     CodeAnalysisManagedDemo プロパティ ページが表示されます。  
  
3.  クリックして **CodeAnalysis**します。  
  
4.  確認して  **ビルドに対するコード分析を有効にする (定数 CODE_ANALYSIS を定義**) がオンになっています。  
  
5.   **この規則セットを実行** ドロップダウン リストで、 **Microsoft のすべてのルール**します。  
  
6.   **ファイル** ] メニューのをクリックして **選択した項目を保存**, 、ManagedDemo のプロパティ ページを閉じます。  
  
7.   **ビルド** ] メニューのをクリックして **ビルド ManagedDemo**します。  
  
     CodeAnalysisManagedDemo プロジェクトのビルド警告が報告された、 **コード分析** と **出力** windows です。  
  
     場合、 **コード分析** ウィンドウが表示されないの **分析** ] メニューの [選択 **Windows** し **コード分析を選択して**します。  
  
## <a name="correct-the-code-analysis-issues"></a>コード分析の問題を修正します。  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>コード分析規則違反を修正するには  
  
1.   **ビュー** ] メニューのをクリックして **エラー一覧**します。  
  
     選択した開発者のプロファイルによってポイントする必要があります **その他のウィンドウ** 上、 **ビュー** ] メニューをクリック **エラー一覧**します。  
  
2.   **ソリューション エクスプ ローラー**, 、クリックして **[すべてのファイル**します。  
  
3.  次に、[プロパティ] ノードを展開し、AssemblyInfo.cs ファイルを開きます。  
  
4.  警告を解決するのにには、次を使用します。  
  
-   [Ca 1014: アセンブリに CLSCompliantAttribute をマークする](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design:"demo"は、CLSCompliantAttribute でマークする必要があり、その値を true にする必要があります。  
  
    -   コードを追加 `using``System;` 、AssemblyInfo.cs ファイルにします。  
  
         次に、コードを追加 `[assembly: CLSCompliant(true)]` AssemblyInfo.cs ファイルの末尾にします。  
  
         プロジェクトをリビルドします。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo(String)。  
  
    -   コンス トラクターを追加 `public demo (String s) : base(s) { }` クラスに `demo`します。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリックのデモ (文字列、例外)。  
  
    -   コンス トラクターを追加 `public demo (String s, Exception e) : base(s, e) { }` クラスに `demo`します。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますデモ (SerializationInfo、StreamingContext) の保護。  
  
    -   コードを追加 `using System.Runtime.Serialization;` Class1.cs ファイルの先頭にします。  
  
         次に、コンス トラクターを追加します。 `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         プロジェクトをリビルドします。  
  
-   [Ca 1032: 標準例外コンス トラクターを実装する](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: このクラスに次のコンス トラクターを追加しますパブリック demo()。  
  
    -   コンス トラクターを追加 `public demo () : base() { }` クラスに `demo`**します。**  
  
         プロジェクトをリビルドします。  
  
-   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'TestCode' に変更すると、空間' プログラム名' の大文字小文字の区別を修正します。  
  
    -   名前空間の大文字と小文字を変更する `testCode` に `TestCode`します。  
  
-   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming:"Demo"に変更すると、型名"demo"の大文字小文字の区別を修正します。  
  
    -   メンバーの名前を変更する `Demo`です。  
  
-   [Ca 1709: 識別子を正しく使い分ける](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Item' に変更すると、メンバー名 ']' の大文字小文字の区別を修正します。  
  
    -   メンバーの名前を変更する `Item`です。  
  
-   [1710: 識別子は正しいサフィックスをいなければなりません](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md): Microsoft.Naming: 名前の変更 'testCode.demo' を '例外' で終了します。  
  
    -   クラスとそのコンス トラクターの名前を変更 `DemoException`します。  
  
-   [Ca 2210: アセンブリは有効な厳密な名前を持つ必要があります](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md): 'ManagedDemo' を厳密な名前のキーで署名します。  
  
    -    **プロジェクト** ] メニューのをクリックして **ManagedDemo プロパティ**します。  
  
         プロジェクトのプロパティが表示されます。  
  
         クリックして **署名**します。  
  
         選択、 **アセンブリに署名** チェック ボックスをオンします。  
  
          **厳密な名前キー ファイルを選択して** 一覧で、[ **\< New… >**します。  
  
          **厳密な名前キーの作成** ] ダイアログ ボックスが表示されます。  
  
          **キー ファイル名**, 、TestKey を入力します。  
  
         パスワードを入力し、クリックして **OK**します。  
  
          **ファイル** ] メニューのをクリックして **選択した項目を保存**, 、プロパティ ページを閉じます。  
  
         プロジェクトをリビルドします。  
  
-   [2237 ca: ISerializable 型を SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: この型が ISerializable を実装して、その 'デモ' を入力する [Serializable] 属性を追加します。  
  
    -   追加、 `[Serializable ()]` 属性をクラス `demo`します。  
  
         プロジェクトをリビルドします。  
  
 変更が完了したら、Class1.cs ファイルは次のようになります。  
  
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
  
    1.  コード分析] ウィンドウで、警告を選択します。  
  
    2.  選択 **アクション**, 、順に選択 **メッセージの非表示**, 、にして **プロジェクト抑制ファイル内**します。  
  
     詳細については、次を参照してください [方法: メニュー項目を使用して警告を抑制する状況。](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  プロジェクトをリビルドします。  
  
     警告またはエラーなしでビルドされるプロジェクトです。