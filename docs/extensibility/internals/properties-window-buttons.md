---
title: "プロパティ ウィンドウのボタン | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[プロパティ] ウィンドウのボタン"
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# プロパティ ウィンドウのボタン
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

開発言語や製品の種類によっては特定のボタンは ENT0ENT \[出力\] ウィンドウのツール バーに既定で表示されます。  いずれの場合も **項目別 \*\*\* Alphabetized \*\*\* プロパティ**  と  **プロパティ ページ**  のボタンが表示されます。  Visual C\# と Visual Basic では\[\] ボタンの ENT0ENT 表示されます。  Visual C\+\+ のプロジェクトでは**\*\*\* VC\+\+ Messages \*\*\*** と **\*\*\* VC Overrides \*\*\*** のボタンが表示されます。  追加のボタンは他の種類のプロジェクトに表示されないことがあります。  \[入力\] ENT2ENT ウィンドウのボタンに関する詳細については[プロパティ ウィンドウ](../../ide/reference/properties-window.md) を参照してください。  
  
## プロパティ ウィンドウのボタンの実装。  
 \[入力\] ENT0ENT ボタンをクリックするとカテゴリ別にプロパティを使用してフォーカスを保持するオブジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> のインターフェイスを呼び出します。  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> は ENT0ENT \[出力\] ウィンドウに表示 `IDispatch` のオブジェクトに対して実行されます。  
  
 負の値である 11 の定義済みプロパティのカテゴリがあります。  カスタム カテゴリを定義できますが定義済みのカテゴリを区別するために正の値を割り当てることをお勧めします。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> のメソッドは指定したプロパティの適切なプロパティのカテゴリの値。  <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> のメソッドはカテゴリ名を含む文字列。  Visual Studio の標準プロパティのカテゴリの値がわかっているためカスタム カテゴリの値だけをサポートする必要があります。  
  
 \[入力\] ENT0ENT ボタンをクリックするとプロパティは名前に基づいてアルファベット順に表示されます。  名前にはローカライズされた並べ替えアルゴリズムに従って `IDispatch` で取得します。  
  
 \[ENT0ENT\] ウィンドウを開くと\[ENT1ENT\] ボタンをクリックすると自動的に表示されます。  環境内の他の部分では同じボタンが表示されます ENT0ENT\[出力\] ウィンドウに示すようにをクリックします。  
  
 `ISpecifyPropertyPages` 選択したオブジェクトに実装する必要 ENT3ENT \[入力\] ボタンを使用できません。  ソリューションとプロジェクトに通常関連付けられたプロパティ ページに表示する構成依存プロパティはプロジェクト項目に関連付けられにすることもできます \(Visual C\+\+\)。  
  
> [!NOTE]
>  \[ENT4ENT\] ウィンドウでアンマネージ コードを使用してツール バー ボタンを追加できません。  ツール バー ボタンを追加するには<xref:System.Windows.Forms.Design.PropertyTab> から派生するマネージ オブジェクトを作成する必要があります。  
  
## 参照  
 [プロパティを拡張します。](../../extensibility/internals/extending-properties.md)