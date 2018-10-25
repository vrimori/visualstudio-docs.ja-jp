---
title: 'チュートリアル: カスタムの構成とルール セット |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5976ee0c0fbfc4befe97f2ab25c46744a8267134
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906053"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>チュートリアル: カスタム規則セットの構成と使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルは、カスタマイズされたを使用するように構成されているコード分析ツールを使用する方法を示します*ルール セット*クラス ライブラリにします。 別の規則のセットを互換性に影響しない方法で解決できる問題のレガシ コードのスキャンなどの特定のニーズを満たすために、ソリューションでは、指定したかを選択するプロジェクトの種類に関連するルール セットを選択できます。 いずれの場合も、ルール セットをプロジェクトの要件に合わせてカスタマイズもできます。  
  
 このチュートリアルでは、これらのプロセスをステップします。  
  
-   クラス ライブラリを作成します。  
  
-   選択、 **Microsoft 基本デザイン ガイドライン規則**コード分析規則セット。  
  
-   クラスには、独自のコードを追加します。  
  
-   コード分析を実行します。  
  
-   規則セットをカスタマイズします。  
  
-   コード分析を実行して、ルール セットのカスタマイズの動作の仕組みを参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、または [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>規則を使用してコード分析設定します。  
 最初に、単純なクラス ライブラリを作成します。  
  
#### <a name="create-a-class-library"></a>クラス ライブラリを作成します。  
  
1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
2. **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類**、 をクリックして**Visual c#** します。  
  
3. **Visual c#**、**クラス ライブラリ**します。  
  
4. **名前**テキスト ボックスに「 **RuleSetSample**順にクリックします**OK**します。  
  
   次に、選択は、 **Microsoft 基本デザイン ガイドライン規則**ルール セットと、プロジェクトで保存します。  
  
#### <a name="select-a-code-analysis-rule-set"></a>コード分析規則セットを選択します。  
  
1. **分析** メニューのをクリックして**RuleSetSample のコード分析を構成する**します。  
  
    コード分析の構成設定が表示されます。  
  
2. **この規則セットを実行**ドロップダウン リストで、 **Microsoft のすべてのルール**します。  
  
    使用可能なルール セットの詳細については、次を参照してください。[コード分析規則セットの参照](../code-quality/code-analysis-rule-set-reference.md)します。  
  
    [ファイル] メニューで、次のようにクリックします。**選択した項目の保存**選択したルール セットに関する情報とその設定で、プロジェクト ファイルを更新します。  
  
   > [!TIP]
   >  コード分析の対象と問題の優先順位付けに使用することをお勧めは最初に、実際の状況で、**最小推奨規則**ルール セットと目的の問題を修正し、段階的に追加複数のルールまたはルールを検出してその他の問題を解決を設定します。  
  
   次に、コードは、ca 1704 の違反を確認するために使用するクラス ライブラリを追加、「識別子は正しく入力されなければなりません」コード分析ルール。 詳細については、次を参照してください。 [ca 1704: 識別子は正しく入力されなければなりません](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)します。  
  
#### <a name="add-your-own-code"></a>独自のコードを追加します。  
  
- ソリューション エクスプ ローラーで、Class1.cs ファイルを開き、既存のコードを次のように置き換えます。  
  
  ```  
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
  
  今すぐ RuleSetSample プロジェクトでコード分析を実行でき、エラーと警告をエラー一覧 ウィンドウで生成された検索できます。  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>RuleSetSample プロジェクトでコード分析を実行します。  
  
1. **分析** メニューのをクリックして**RuleSetSample でコード分析を実行**します。  
  
2. エラー一覧 ウィンドウで次のようにクリックします。**警告**順にクリックします、**説明**列ヘッダーの警告を並べ替えるに並びます。  
  
    実際のアプリケーションではこの時点では、修正する必要のルール違反を修正または必要に応じてオフにするや価値修正されなかったことを確認する場合のルールを抑制します。 詳細については、次を参照してください。 [SuppressMessage 属性使用での警告を抑制する](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)します。  
  
3. Ca 1704 警告に注意してください。 このルールでこれらの違反を示すこと検討してください"のパラメーターのわかりやすい名前を提供する" コードで問題を解決する可能性がありますか、次の手順で説明したように、ルールを無効にできます。  
  
   次に、ca 1704 の警告を除外する設定のルールのカスタマイズを「識別子は正しく入力されなければなりません」します。  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>特定のルールを無効にするプロジェクトの設定ルールをカスタマイズします。  
  
1. **分析** メニューのをクリックして**RuleSetSample のコード分析を構成する**します。  
  
2. **この規則セットを実行**ドロップダウン ボックスの一覧であることを確認、 **Microsoft のすべてのルール**ルールのセットは強調表示をクリックして**オープン**。 規則セットのページが表示されます。  
  
3. Microsoft.Naming カテゴリ ノードを展開し、ca 1704 の警告を選択します。  
  
4. で、**アクション**列で、**なし。** これは ca 1704 が警告またはエラー一覧 ウィンドウでエラーとして表示することを防ぎます。  
  
    さまざまなツール バー ボタンを実験するよい機会になり、フィルター オプションの理解を深めるにようになりました。 たとえば、使用することができます、 **Group By**特定の規則または規則のカテゴリを検出するためのドロップダウン リスト。 別の例として使用できる、**無効化されたルールを非表示に**ですべての規則を表示または非表示にルール セットのページのツールバーのボタン、**アクション**列に設定**None**します。 無効にすることも確認をオフにしている規則をスキャンする場合に役立ちます。 ことができます。  
  
5. [表示] メニューで、[プロパティ] ウィンドウをクリックします。 型**カスタム規則セットのマイ**プロパティ ツール ウィンドウの [名前] ボックスにします。 これにより、変更、新しいルール セットの表示名、 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE。  
  
6. **ファイル** メニューのをクリックして**保存の Microsoft すべて Rules.ruleset**カスタマイズされた規則を保存するには設定します。 プロジェクトのルート フォルダーに移動します。 **ファイル名**テキスト ボックスに「 **MyCustomRuleSet**します。 カスタム規則セットは、プロジェクトで使用するためここで選択できます。  
  
   新しい規則セットが作成されたのようになりました 新しい規則のセットを使用することを指定するプロジェクトの設定を構成する必要があります。  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>プロジェクトで使用するために設定する新しい規則を指定します。  
  
1. ソリューション エクスプ ローラーでプロジェクトを右クリックしを選択し、**プロパティ**します。  
  
2. **プロパティ**] タブで [**コード分析**します。  
  
    **この規則セットを実行**ドロップダウン リストでは、をクリックして**\<参照.>** します。 コード プロジェクトのルート フォルダーに移動し、 **MyCustomRuleSet.ruleset**します。 これは、前の手順で作成した新しいルール セットです。  
  
3. **ファイル** メニューのをクリックして**保存**プロジェクト構成を保存します。 カスタム規則セットは、プロジェクトを今すぐ使用できます。  
  
   最後に、もう一度、MyCustomRuleSet 規則セットを使用してコード分析を実行します。 Ca 1704 のパフォーマンス規則違反をエラー一覧 ウィンドウが表示されないことに注意してください。  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>コード分析を RuleSetSample プロジェクトを 2 回目の実行します。  
  
1.  **分析** メニューのをクリックして**RuleSetSample でコード分析を実行**します。  
  
2.  エラー一覧 ウィンドウで、注意をクリックすると**警告**、「識別子は正しく入力されなければなりません」ルールの ca 1704 警告違反が表示されません。  
  
## <a name="see-also"></a>関連項目  
 [方法: マネージ コード プロジェクトのコード分析を構成します。](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [コード分析規則セットの参照](../code-quality/code-analysis-rule-set-reference.md)



