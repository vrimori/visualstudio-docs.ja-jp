---
title: "コード分析チェックイン ポリシーの作成と |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b7187ef8d3342ad050c66debf939e9c6a6213957
ms.sourcegitcommit: e5bd950df79175a96fe62b3d4b17a3ef536ec4c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>コード分析を用いたチェックイン ポリシーの作成と使用
Team Foundation バージョン管理 (TFVC: Team Foundation Version Control) を使用すると、チーム プロジェクト内の .NET Framework とネイティブ (C/C++) コード プロジェクトに適したコード分析のチェックイン ポリシーを作成できます。 コード分析を用いたチェックイン ポリシーを使用することにより、コード ベースにチェックインされるコードを管理し、品質を高めることができます。  
  
 ローカルのビルドが最新の状態で、コード分析が最新のソース ファイル上で実行されている場合は、チェックイン ポリシーで合格と見なされます。 コード プロジェクト内で有効に設定されるコード分析については、少なくともチーム プロジェクトのチェックイン ポリシー内で定義された規則と同じ規則を定義する必要があります。 [チーム プロジェクトの設定] でエラーとして指定された規則は、コード プロジェクト内においてもエラーとして指定する必要があります。  
  
> [!IMPORTANT]
>  コード分析チェックイン ポリシーを Web サイト プロジェクトに適用することはできません。 これらのポリシーは、Web アプリケーション プロジェクトに適用できます。  
  
 [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]のチーム プロジェクトの設定を使用して、コード分析を用いたチェックイン ポリシーを作成します。 チェックイン ポリシーはチーム プロジェクトに対して指定され、適用されますが、コード分析はローカルの開発用コンピューター上の各コード プロジェクトに対して構成され、実行されます。 このセクションでは、コード分析を用いたチェックイン ポリシーをチーム プロジェクト用に指定する方法と、カスタム コード分析ポリシーをマネージ コード用に実装する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 標準のコード分析チェックイン ポリシーを作成または更新する](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 コード分析ポリシーをチーム プロジェクト用に設定および変更するための手順を説明します。  
  
 [マネージ コード用のカスタム チェックイン ポリシーの実装](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 カスタム規則セットをチーム プロジェクトのマネージ コード用に作成するための手順と、チェックイン ポリシーを使用してチーム プロジェクトのコード プロジェクトを同期する方法について説明します。  
  
 [コード分析を用いたチェックイン ポリシーに関するバージョンの互換性](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)] の異なるバージョン間におけるコード分析チェックインの互換性の問題について説明します。  
  
 [方法 : コード分析辞書をカスタマイズする](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 コード分析の名前付け規則で参照される辞書に単語とトークンを追加する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)