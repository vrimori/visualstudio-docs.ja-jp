---
title: "入れ子のプロジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクトの入れ子"
  - "入れ子になったプロジェクト"
  - "プロジェクト [Visual Studio SDK] の子プロジェクトします。"
  - "入れ子のプロジェクト [Visual Studio SDK]"
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 入れ子のプロジェクト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VS パッケージを使用するエンタープライズ アプリケーション開発者が類似した種類のプロジェクトでまとめてグループ化できます便利なことに [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を使用して *プロジェクトの入れ子*します。 たとえば、エンタープライズ テンプレート プロジェクトは、カテゴリにプロジェクトをグループ化の入れ子になったプロジェクトを使用します。 ビジネス ファサード プロジェクトや Web UI プロジェクトの場合は、1 つのカテゴリにグループ化。  
  
 このシナリオではありません、開発者が各親プロジェクトの下でネストできますプロジェクトの数に対する制限、開発者は、制限プログラムを提供します。 このグループの種類もが再帰的で、サブプロジェクトの親である子の下位に子 \[場合に子プロジェクトと同じ種類のプロジェクトを入れ子にすることができます。  
  
 プロジェクトの入れ子がの組み込みの一部ではない [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 子プロジェクト内の入れ子のサブプロジェクトをネストを有効にし、コードを記述する必要があります。 親プロジェクトがある特別な vs パッケージまたはプロジェクトの種類を作成し、プロジェクトの入れ子を実装するために必要なコードが含まれる、独自の GUID に登録されています。  
  
 C\# Example.Nested プロジェクト サンプルに入れ子になったプロジェクトの例が表示されます。  
  
## 入れ子になったプロジェクトの使用例  
 ![入れ子のプロジェクト ソリューション](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
入れ子になったプロジェクトの使用例  
  
## 参照  
 [方法: 入れ子になったプロジェクトの実施](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [入れ子になったプロジェクトのアンロードと再ロードに関する考慮事項](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [ウィザードでサポートされる入れ子のプロジェクト](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [入れ子になったプロジェクトに対するコマンド処理を実装します。](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [入れ子になったプロジェクトを AddItem\] ダイアログ ボックスのフィルター処理](../Topic/Filtering%20the%20AddItem%20Dialog%20Box%20for%20Nested%20Projects.md)   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)