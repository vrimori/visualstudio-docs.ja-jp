---
title: "ウィザード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: af0466ea3c11b75090e45cb9b408ed0723cd8a6f
ms.lasthandoff: 02/22/2017

---
# <a name="wizards"></a>ウィザード
追加するウィザードを作成したら、通常、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) を他のユーザーが使用できるようにします。 追加のウィザードが表示されます、**新しいプロジェクトの追加**または**新しい項目の追加**ダイアログ ボックス。 表示する、**新しいプロジェクトの追加**または**新しい項目の追加** ダイアログ ボックスで開いているソリューションを右クリックして**ソリューション エクスプ ローラー**、 をポイント**追加**、順にクリック**新しいプロジェクト**または**新しい項目の**です。  
  
 ウィザードを実装する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザーができるようにを開くときに使用できる値のツリー ビューの中から選択、**新しいプロジェクトの追加** ダイアログ ボックスまたは**新しい項目の追加** ダイアログ ボックス内の項目を右クリックすると、または**ソリューション エクスプ ローラー**します。  
  
 ウィザードで ite、または新しいプロジェクトの名前をローカライズするオプションを指定して、ウィザードを選択したときにユーザーが表示されるアイコンを決定することができます。 使用可能なその他の項目の基準とした新しい項目が表示される順序を制御することもできます。項目は、アルファベット順に整理することはありません。  
  
 開かれたときに、ウィザードに渡されるカスタムのパラメーターに基づいて異なる方法で開始するウィザードを指定することもできます。  
  
 このセクションのトピックが発生するために実装ファイル、ディスカッション、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **新しいプロジェクトの追加**と**新しい項目の追加**ダイアログ ボックスを使用できるウィザードとテンプレートや、IDE で正しく動作するように、ウィザードが満たす必要のある要件の間で、ウィザードを一覧表示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テンプレートのディレクトリの説明 (します。Vsdir) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 ディレクトリの記述ファイルにどのようなテンプレートの概要を説明し、フォルダー、ウィザードの .vsz ファイル、およびダイアログ ボックスで、プロジェクトに関連付けられているテンプレート ファイルを表示するための IDE で正常に実行する方法について説明します。  
  
 [ウィザード (します。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)  
 IDE でウィザードを開始する方法について説明し、.vsz ファイルの&3; つの部分を示します。  
  
 [ウィザードのインターフェイス (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 説明、`IDTWizard`インターフェイス ウィザードは、IDE で機能するために実装する必要があります。  
  
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)  
 ウィザードの実装方法と、IDE では、実装にコンテキスト パラメーターを渡すときの動作について説明します。  
  
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)  
 カスタム パラメーターを使用して、ウィザードを起動した後、ウィザードの操作を制御する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクトの種類](../../extensibility/internals/project-types.md)  
 新しいプロジェクトの種類をデザインする方法に関する情報を提供するその他のトピックへのリンクを提供します。  
  
 [チュートリアル: ウィザードの作成](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 ウィザードを作成する方法を示します。  
  
 [プロジェクトの拡張](../../extensibility/extending-projects.md)  
 使用する方法について説明[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プロジェクトとソリューションのコード ファイルとリソース ファイルとソース管理を実装する方法を整理します。
