---
title: 'チュートリアル: 構成および使用するカスタム ルール セット |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b72a86f10c6e864406929fdccfb59bdd9393752e
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>チュートリアル: カスタム規則セットの構成と使用

このチュートリアルは、カスタマイズされたを使用するように構成されているコード分析ツールを使用する方法を示します*ルール セット*クラス ライブラリにします。 互換性に影響しない方法で解決できる問題のレガシ コードをスキャンなどの特定のニーズを満たすために別の規則のセットを選択または、ソリューションの指定したプロジェクトの種類に関連するルール セットを選択できます。 どちらの場合、規則セットは、プロジェクトの要件に微調整するもカスタマイズできます。  
  
このチュートリアルでは、これらのプロセスがステップされます。  
  
-   クラス ライブラリを作成します。  
  
-   選択、 **Microsoft 基本デザイン ガイドライン規則**コード分析規則セットです。  
  
-   クラスには、独自のコードを追加します。  
  
-   コード分析を実行します。  
  
-   規則セットをカスタマイズします。  
  
-   コード分析を実行して、ルール セットのカスタマイズの動作の仕組みを参照してください。  
  
## <a name="using-rule-sets-with-code-analysis"></a>コード分析による規則を使用して設定します。

最初に、単純なクラス ライブラリを作成します。  
  
### <a name="create-a-class-library"></a>クラス ライブラリを作成します。  
  
1.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]**をクリックします。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類**をクリックして**Visual c#**です。  
  
3.  **Visual c#****クラス ライブラリ**です。  
  
4.  **名前**テキスト ボックスで、「 **RuleSetSample**順にクリック**OK**です。  
  
 次に、選択は、 **Microsoft 基本デザイン ガイドライン規則**ルール セットと、プロジェクトを保存します。  
  
### <a name="select-a-code-analysis-rule-set"></a>コード分析規則セットを選択します。  
  
1.  **分析** メニューのをクリックして**RuleSetSample のコード分析を構成する**です。  
  
     コード分析の構成設定が表示されます。  
  
2.  **この規則セットを実行**ドロップダウン リストで、 **Microsoft すべてルール**です。  
  
     使用可能なルール セットの詳細については、次を参照してください。[コード分析規則セットの参照](../code-quality/code-analysis-rule-set-reference.md)です。  
  
     [ファイル] メニューをクリックして**選択した項目の保存**プロジェクト ファイルを選択したルール セットに関する情報とその設定を更新します。  
  
    > [!TIP]
    >  コード分析の対象となる問題の優先順位付けに使用することをお勧めは最初に、実際の状況で、**最小推奨規則**ルール セットと、必要な問題を解決し、増分追加ルールまたはルールの詳細設定を見つけて、その他の問題を修正します。  
  
 次に、いくつかのコードを ca 1704 の違反を示すために使用されるクラス ライブラリに追加するは「識別子は正しく入力されなければなりません」コード分析ルール。 詳細については、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)です。  
  
### <a name="add-your-own-code"></a>独自のコードを追加します。  
  
-   ソリューション エクスプローラで、Class1.cs ファイルを開き、次のように、既存のコードを交換します。  
  
    ```csharp
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace RuleSetSample  
    {  
        public class Class1  
        {  
            //The variable parameter names "a" and "b" will cause  
            //the warning CA 1704 Microsoft.Naming "Consider   
            //providing a more meaningful name" to fire  
            public int AddIntegers(int a, int b)  
            {  
  
                int sum = a + b;  
  
                return (sum);  
            }  
        }  
    }
    ```
  
今すぐ RuleSetSample プロジェクトでコード分析を実行し、エラーとエラー一覧 ウィンドウで生成された警告を検索できます。  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>RuleSetSample プロジェクトでコード分析を実行します。  
  
1.  **分析** メニューのをクリックして**RuleSetSample でコード分析を実行**です。  
  
2.  [エラー一覧] ウィンドウ**警告**をクリックし、**説明**列を並べ替えるヘッダーを警告英数字順です。  
  
     実際のアプリケーションではこの時点では、修正する必要のルール違反の修正または必要に応じてをオフにするまたはしたすべき解決されなかったことを確認する場合は、ルールを抑制します。 詳細については、次を参照してください。[警告を抑制する](../code-quality/in-source-suppression-overview.md)です。
  
3.  Ca 1704 警告に注意してください。 このルールでこの規則違反を示すを検討してください"のパラメーターのわかりやすい名前を指定する" コードで、問題を解決する可能性がありますか、次の手順で説明するよう、ルールを無効にすることができます。  
  
 次に、設定、ca 1704 警告を除外するルールをカスタマイズする、「識別子は正しく入力されなければなりません」です。  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>特定のルールを無効にするようにプロジェクトの規則セットをカスタマイズします。  
  
1.  **分析** メニューのをクリックして**RuleSetSample のコード分析を構成する**です。  
  
2.  **この規則セットを実行**ドロップダウン ボックスの一覧であることを確認、 **Microsoft すべてルール**規則のセットが強調表示されていると、をクリックして**開く**です。 規則セットのページが表示されます。  
  
3.  Microsoft.Naming カテゴリ ノードを展開し、ca 1704 警告を選択します。  
  
4.  下にある、**アクション**列をオン**なし。** これは ca 1704 が警告またはエラー一覧 ウィンドウでエラーとして表示することを防ぎます。  
  
     さまざまなツール バー ボタンをテストする絶好のタイミングや、フィルターの理解を深めるオプションようになりました。 たとえば、使用することができます、 **Group By**ドロップダウン リストに特定の規則または規則のカテゴリの検索に役立ちます。 別の例は、使用できること、**無効化されたルールの非表示に**ですべての規則を表示または非表示には、ルール セット ページ ツールバーにボタン、**アクション**列に設定**None**です。 確認することも無効にして無効にしているすべてのルールをスキャンする場合に役立ちます。 これができます。  
  
5.  [表示] メニューで、[プロパティ] ウィンドウをクリックします。 型**カスタム規則セットのマイ**プロパティの [ツール] ウィンドウの [名] ボックスにします。 これにより、新しいルール セットの表示名が変更、 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE です。  
  
6.  **ファイル** メニューのをクリックして**保存の Microsoft すべて Rules.ruleset**セットをカスタマイズした規則を保存します。 プロジェクトのルート フォルダーに移動します。 **、FileName**テキスト ボックスで、「 **MyCustomRuleSet**です。 カスタム規則セットは、プロジェクトで使用するようになりました選択できます。  
  
新しいルール セットが作成されたのようになりましたがある、新しい規則のセットを使用することを指定するプロジェクト設定を構成します。  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>プロジェクトを使用する設定の新しいルールを指定します。  
  
1.  ソリューション エクスプ ローラーでプロジェクトを右クリックし、**プロパティ**です。  
  
2.  **プロパティ** タブで、をクリックして**コード分析**です。  
  
     **この規則セットを実行**ドロップダウン リストをクリックして**\<参照.>**です。 コード プロジェクトのルート フォルダーに移動し、 **MyCustomRuleSet.ruleset**です。 これは、前の手順で作成した新しいルール セットです。  
  
3.  **ファイル** メニューのをクリックして**保存**をプロジェクトの構成を保存します。 カスタム規則セットは、プロジェクトを今すぐ使用できます。  
  
 最後に、もう一度、MyCustomRuleSet 規則セットを使用してコード分析を実行します。 Ca 1704 パフォーマンス規則違反をエラー一覧 ウィンドウが表示されないことに注意してください。  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>2 回目の RuleSetSample プロジェクトでコード分析を実行します。  
  
1.  **分析** メニューのをクリックして**RuleSetSample でコード分析を実行**です。  
  
2.  エラー一覧 ウィンドウでことに注意してをクリックすると**警告**、「識別子は正しく入力されなければなりません」ルールの ca 1704 警告違反は、不要になったを参照してください。  
  
## <a name="see-also"></a>関連項目

[方法: マネージ コード プロジェクトのコード分析を構成します。](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[コード分析規則セットの参照](../code-quality/code-analysis-rule-set-reference.md)