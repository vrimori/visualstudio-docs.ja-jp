---
title: '方法: 標準のコード分析チェックイン ポリシーを作成または |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f4e834eb02c30bee0fedfa90ddb17d3fa766fb1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544314"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>方法: 標準のコード分析チェックイン ポリシーを作成または更新する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: を作成または更新プログラムの標準的なコード分析チェックイン ポリシー](https://docs.microsoft.com/visualstudio/code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies)します。  
  
コード分析チェックイン ポリシーを使用してチーム プロジェクト内のすべてのコード プロジェクトでコード分析を実行することを要求することができます。 コード分析を必要とすると、コード ベースにチェックインされているコードの品質を向上させることができます。  
  
> [!NOTE]
>  この機能は Team Foundation Server を使用している場合にのみ使用できます。  
  
 コード分析チェックイン ポリシーは、チーム プロジェクトの設定で設定され、チーム プロジェクト内の各コード プロジェクトに適用されます。 コード分析の実行は、コード プロジェクトのプロジェクト (.xxproj) ファイル内のコード プロジェクトに対して構成されます。 コード分析の実行は、ローカル コンピューターで実行されます。 ルールは、チーム プロジェクトの設定をコンピューターで実行する必要がありますコード分析チェックイン ポリシーを有効にするし、最後に編集した後にチェックインされるコード プロジェクト内のファイルをコンパイルする必要がありますには、少なくとも、コード分析の実行を含む、c変更が加えられました。  
  
-   マネージ コードを指定してチェックイン ポリシーを設定する、*ルール セット*コード分析規則のサブセットを格納しています。  
  
-   C/C++ のコードでは、チェックイン ポリシーでは、すべてのコード分析規則を実行することが必要です。 チーム プロジェクト内の個々 のコード プロジェクトの特定のルールを無効にするプリプロセッサ ディレクティブを追加できます。  
  
 マネージ コードのチェックイン ポリシーを指定すると後、チーム メンバーは、チーム プロジェクトのポリシー設定をコード プロジェクト、コード分析設定を同期できます。  
  
### <a name="to-open-the-check-in-policy-editor"></a>チェックイン ポリシー エディターを開く  
  
1.  チーム エクスプ ローラーで、チーム プロジェクト名を右クリックして**チーム プロジェクトの設定**、 をクリックし、**ソース管理**します。  
  
2.  **ソース管理**ダイアログ ボックスで、**チェックイン ポリシー**タブ。  
  
3.  次のいずれかの操作を行います。  
  
    -   クリックして**追加**新しいチェックイン ポリシーを作成します。  
  
    -   既存をダブルクリックして**コード分析**内の項目、**ポリシーの種類**ポリシーを変更する ボックスの一覧。  
  
### <a name="to-set-policy-options"></a>ポリシー オプションを設定するには  
  
-   選択するか、次のオプションをオフにします。  
  
    |オプション|説明|  
    |------------|-----------------|  
    |**現在のソリューションの一部であるファイルのみを含むチェックインを強制します。**|コード分析は、ソリューションおよびプロジェクトの構成ファイルで指定されたファイルでのみ実行できます。 このポリシーは、ソリューションの一部であるすべてのコードを分析することが保証されます。|  
    |**C/C++ コード分析を強制 (/analyze)**|すべての C または C++ プロジェクトをビルドすることが必要です、/analyze コンパイラ オプションがチェックインされる前に、コード分析を実行します。|  
    |**マネージ コードのコード分析を適用します。**|すべてのマネージ プロジェクトはコード分析を実行しがチェックインされる前に、ビルドが必要です。|  
  
-  
  
### <a name="to-specify-a-managed-rule-set"></a>"マネージ"規則セットを指定するには  
  
-   **この規則セットを実行**一覧で、次の方法のいずれかを使用します。  
  
    -   Microsoft の標準規則セットを選択します。  
  
    -   カスタム規則セットを選択する をクリックして **\<... にソース管理からのルール セットの選択 >**、し、ソース コントロールのブラウザーで、規則セットのバージョン コントロール パスを入力します。 バージョン コントロール パスの構文です。  
  
    -   **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    -   セットを作成し、カスタム チェックイン ポリシーの規則を実装する方法の詳細についてを参照してください[マネージ コードを実装するカスタム チェックイン ポリシー](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)します。  
  
## <a name="see-also"></a>関連項目  
 [コード分析を用いたチェックイン ポリシーの作成と使用](../code-quality/creating-and-using-code-analysis-check-in-policies.md)



