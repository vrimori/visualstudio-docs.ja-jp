---
title: ウィザード |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22aa4c86cc00b57e7c290d8b5a5655713ee05052
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955363"
---
# <a name="wizards"></a>ウィザード
通常、ウィザードを作成した後に追加する、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]他のユーザーが使用できるように開発環境 (IDE) を統合します。 追加のウィザードは、表示されます、**新しいプロジェクトの追加**または**新しい項目の追加** ダイアログ ボックス。 表示する、**新しいプロジェクトの追加**または**新しい項目の追加** ダイアログ ボックスで開いているソリューションを右クリックして**ソリューション エクスプ ローラー**、 をポイント**追加**とクリックして**新しいプロジェクト**または**新しい項目の**します。  
  
 ウィザードを実装することができます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]してもらうために開いたときに使用可能な値のツリー ビューから選択、**新しいプロジェクトの追加** ダイアログ ボックスまたは**新しい項目の追加**ダイアログ ボックスで、または、右クリック内の項目**ソリューション エクスプ ローラー**します。  
  
 ウィザードでは、ite 用、または新しいプロジェクトの名前をローカライズするオプションを指定して、ウィザードを選択したときにユーザーが表示されるアイコンを指定できます。 使用可能な項目に対するその他の新しい項目が表示される順序を制御することもできます。項目は、アルファベット順で整理する必要はありません。  
  
 開かれたときに、ウィザードに渡されるカスタムのパラメーターに基づいて異なる方法で開始するウィザードを指定することもできます。  
  
 このセクションのトピックで発生するために実装するファイル、ディスカッション、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **新しいプロジェクトの追加**と**新しい項目の追加**ダイアログ ボックスを使用できるウィザードとテンプレート間で、ウィザードを一覧表示IDE で正常に動作するウィザードが満たす必要のある要件です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テンプレート ディレクトリの説明 (.Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 ディレクトリの記述ファイル テンプレートの概要を説明し、フォルダー、ウィザードの .vsz ファイル、およびダイアログ ボックスで、プロジェクトに関連付けられているテンプレート ファイルを表示するための IDE でその機能について説明します。  
  
 [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)  
 IDE でウィザードを起動する方法について説明し、.vsz ファイルの 3 つの部分を一覧表示されます。  
  
 [ウィザード インターフェイス (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 について説明します、`IDTWizard`インターフェイス ウィザードは、IDE で作業するために実装する必要があります。  
  
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)  
 ウィザードの実装方法と、IDE では、実装にコンテキスト パラメーターを渡す場合の処理について説明します。  
  
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)  
 カスタム パラメーターを使用して、ウィザードを起動した後、ウィザードの操作を制御する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクト タイプ](../../extensibility/internals/project-types.md)  
 新しいプロジェクトの種類を設計する方法についての情報を提供するその他のトピックへのリンクを提供します。  
  
 [プロジェクトの拡張](../../extensibility/extending-projects.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトおよびソリューションを使用してコード ファイルとリソース ファイルを編成する方法、またソース管理を実装する方法について説明します。