---
title: "ワークフロー デザイナーを使用して XAML をデバッグする方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ワークフロー デザイナーを使用して XAML をデバッグする方法
ワークフローは XAML で定義されます。ワークフローの UI 表現は、ワークフローを定義する XAML ツリーに基づいて構築されます。デバッグ作業は、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]でのワークフローのデバッグと同様です。たとえば、XAML のデバッグ中に、ローカル、ウォッチ、およびスレッドの各ウィンドウは、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]でのデバッグ時と同様に機能します。また、XAML のデバッグ中に使用される呼び出し履歴ビューは、ワークフローの実行フローの行ベースの階層ビューです。  
  
> [!NOTE]
>  ワーク フローの XAML はアクティビティと同じアセンブリ内にある場合は、クラス名のアセンブリの部分は含まれません。クラス \(アクティビティ\) の名前のこの部分がないと、XAML をランタイムに読み込むことができません。メイン プロジェクトと同じ名前空間にアクティビティを定義することは推奨されません。そうでなければ、XAML はデザイナーで編集した後で手動で編集する必要があります。  
  
### ワークフローの XAML をデバッグするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でワークフロー プロジェクトまたはアクティビティ プロジェクトを開きます。  
  
2.  「[ワークフロー内にブレークポイントを設定する方法](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)」の説明に従って、デバッグ対象のアクティビティにブレークポイントを設定します。  
  
3.  ワークフロー定義を含む .xaml ファイルを右クリックし、**\[コードの表示\]** をクリックします。デザイン ビューでブレークポイントを設定したアクティビティの XAML 要素宣言と同じ行に、ブレークポイントが表示されます。  
  
4.  「[ワークフロー デバッガーを呼び出す方法](../workflow-designer/how-to-invoke-the-workflow-debugger.md)」の説明に従ってデバッガーを起動します。  
  
5.  コードがいずれかのブレークポイントまで実行されると、そのブレークポイントに関連付けられている XAML 要素が強調表示されます。次のブレークポイントに移動するには、F10 キーまたは F11 キーを使用します。  
  
## 参照  
 [ワークフロー内にブレークポイントを設定する方法](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [ワークフロー デバッガーを呼び出す方法](../workflow-designer/how-to-invoke-the-workflow-debugger.md)