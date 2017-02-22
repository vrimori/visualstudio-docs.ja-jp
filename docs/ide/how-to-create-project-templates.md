---
title: "方法 : プロジェクト テンプレートを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ExportTemplateWizard"
helpviewer_keywords: 
  - "プロジェクト テンプレート, 作成"
  - "プロジェクト テンプレート, カスタム テンプレートの位置"
  - "プロジェクト テンプレート, メタデータ ファイル"
  - "Visual Studio のテンプレート, 作成 (プロジェクト テンプレートの)"
  - "Visual Studio のテンプレート, プロジェクト テンプレート"
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : プロジェクト テンプレートを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

次の手順に従うと、**テンプレートのエクスポート** ウィザードを使用してテンプレートを作成できます。このウィザードでは、テンプレートを .zip ファイルにパッケージ化します。  また、向上した配置用の VSIX 形式でテンプレートのエクスポート ウィザード拡張を、または [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]に含まれているテンプレートを使用して作成することも、テンプレートを手動で作成できます。  
  
### 標準のテンプレートのエクスポート ウィザードを使用してカスタム プロジェクト テンプレートを作成するには  
  
1.  プロジェクトを作成します。  
  
    > [!NOTE]
    >  テンプレートのソースになるプロジェクトに名前を付けるときは、有効な識別子文字のみを使用します。  無効な文字を含んでいる名前のプロジェクトからエクスポートされたテンプレートは、そのテンプレートに基づいて後で作成するプロジェクトのコンパイル エラーの原因になる可能性があります。  有効な識別子文字の詳細については、「[Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)」を参照してください。  
  
2.  プロジェクトを編集して、テンプレートとしてエクスポートする準備をします。  
  
3.  適宜、コード ファイルを編集して、パラメーター置換を行う場所を示します。  パラメーターの置換の詳細については、「[方法 : テンプレート内のパラメーターを置き換える](../ide/how-to-substitute-parameters-in-a-template.md)」を参照してください。  
  
4.  **\[ファイル\]** メニューの **\[テンプレートのエクスポート\]** をクリックします。  **テンプレートのエクスポート** ウィザードが開きます。  
  
5.  **\[プロジェクト テンプレート\]** をクリックします。  
  
6.  現在のソリューションに複数のプロジェクトがある場合は、テンプレートにエクスポートするプロジェクトを選択します。  
  
7.  **\[次へ\]** をクリックします。  
  
8.  テンプレートのアイコンとプレビュー イメージを選択します。  これらは **\[新しいプロジェクト\]** ダイアログ ボックスに表示されます。  
  
9. テンプレート名および説明を入力します。  
  
10. **\[完了\]** をクリックします。  プロジェクトは .zip ファイルにエクスポートされ、指定した出力場所に配置されます。選択すると、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] にインポートされます。  
  
     [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] をインストールした場合は、完成したテンプレートを .vsix ファイルにラップして、**VSIX プロジェクト** テンプレートを使用して配置を行うことができます。  詳細については、「[VSIX プロジェクトのテンプレートの概要](../extensibility/getting-started-with-the-vsix-project-template.md)」を参照してください。  
  
## 参照  
 [カスタム プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [方法 : 項目テンプレートを作成する](../ide/how-to-create-item-templates.md)