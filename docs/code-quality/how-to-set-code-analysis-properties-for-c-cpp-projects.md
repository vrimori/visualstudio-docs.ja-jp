---
title: "方法: C と C++ プロジェクトのコード分析のプロパティを設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 629bc4dc36ade84f6a6e55518775f0d11165da7c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>方法: C/C++ プロジェクトのコード分析プロパティを設定する
コード分析ツールの構成ごとに、プロジェクトのコードを分析に使用する規則を構成することができます。 さらに、生成され、サード パーティ製ツールを使用して、プロジェクトに追加されたコードからの警告を抑制するコード分析を指示することができます。  
  
## <a name="code-analysis-property-page"></a>コード分析 プロパティ ページ  
 **コード分析**プロパティ ページには、プロジェクトのすべてのコード分析の構成設定が含まれています。 開くには、コード分析] プロパティ ページで、プロジェクトの**ソリューション エクスプ ローラー**プロジェクトを右クリックし、[クリックして**プロパティ**です。 次に、展開**構成プロパティ**を選択し、**コード分析**タブです。  
  
## <a name="project-configuration-and-platform"></a>プロジェクト構成とプラットフォーム  
 **構成**リストと**プラットフォーム**リストでは、別のプロジェクトの構成とプラットフォームの組み合わせに別のコード分析設定を適用することができます。 たとえば、プロジェクトをデバッグする 1 つの規則のセットを適用するコード分析がビルドされ、一連の異なるリリース ビルドを指示できます。  
  
## <a name="enabling-code-analysis"></a>コード分析を有効にします。  
 選択して、プロジェクトのコード分析を有効にするかどうかを決定できます**を有効にするコード分析の C と C++ のビルドで**です。 組み合わせて、**構成** ボックスの一覧、たとえば、ことがデバッグ ビルドと、リリース ビルドを有効にするコード分析を無効にします。  
  
 プロジェクトにマネージ コードが含まれている場合、有効にするにまたはを選択すると、コード分析を無効にするかどうかを決定できます**ビルドに対するコード分析を有効にする**です。  
  
 コード分析は、コードの品質向上およびよくある落とし穴を回避するために設計されています。 そのため、慎重に検討するコード分析を無効にするかどうか。 通常の規則セットを無効にすることをお勧めまたはしないようにする個々 のルールは、プロジェクトに適用します。  
  
## <a name="generated-code"></a>生成されたコード  
 開発者は、アプリケーションをすばやく開発するのに役立つツールを頻繁に使用します。 これらのツールは、プロジェクトに追加されるコードを生成できます。 生成されたコードでは、検出コード分析規則違反を表示する場合があります。 ただし、コードを保守したくない場合に参照しない可能性があります。  
  
 **から生成されたコードの結果を抑制する状況**チェック ボックスをオン、**全般** プロパティ ページがサード パーティ製ツールによって生成されるマネージ コードからのコード分析の警告を表示するかどうかを選択することができます.  
  
## <a name="rule-sets"></a>規則セット  
 ルール セットを選択して、コード分析で適用する規則を選択することができます、プロジェクトには、マネージ コードが含まれている場合、**この規則セットを実行** ボックスの一覧です。  
  
## <a name="see-also"></a>参照  
 [マネージ コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [C/C++ コードの警告に対応するコードの分析](../code-quality/code-analysis-for-c-cpp-warnings.md)