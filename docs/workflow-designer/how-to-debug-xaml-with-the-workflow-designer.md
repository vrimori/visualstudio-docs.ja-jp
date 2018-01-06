---
title: "方法: ワークフロー デザイナーで XAML をデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: uwp
ms.openlocfilehash: 32144a651fe9178da8bc87a10377e2c4d086d398
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>ワークフロー デザイナーを使用して XAML をデバッグする方法
ワークフローは XAML で定義されます。 ワークフローの UI 表現は、ワークフローを定義する XAML ツリーに基づいて構築されます。 デバッグ作業は、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]でのワークフローのデバッグと同様です。 たとえば、XAML のデバッグ中に、ローカル、ウォッチ、およびスレッドの各ウィンドウは、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]でのデバッグ時と同様に機能します。 また、XAML のデバッグ中に使用される呼び出し履歴ビューは、ワークフローの実行フローの行ベースの階層ビューです。  
  
> [!NOTE]
>  ワークフローの XAML がアクティビティと同じアセンブリ内にある場合、クラス名のアセンブリ部分は含まれません。 クラス (アクティビティ) 名のこの部分がないと、実行時に XAML を読み込むことはできません。 メイン プロジェクトと同じ名前空間でアクティビティを定義することはお勧めしません。定義した場合は、XAML をデザイナーで編集した後に手動で編集する必要があります。  
  
### <a name="to-debug-workflow-xaml"></a>ワークフローの XAML をデバッグするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でワークフロー プロジェクトまたはアクティビティ プロジェクトを開きます。  
  
2.  アクティビティまたは」の説明に従ってをデバッグするアクティビティにブレークポイントを設定[する方法: ワークフロー内のブレークポイントの設定](../workflow-designer/how-to-set-breakpoints-in-workflows.md)です。  
  
3.  ワークフロー定義と選択を含む .xaml ファイルを右クリックして**コードの表示**です。 デザイン ビューでブレークポイントを設定したアクティビティの XAML 要素宣言と同じ行に、ブレークポイントが表示されます。  
  
4.  」の説明に従って、デバッガーを呼び出す[する方法: ワークフロー デバッガーを呼び出す](../workflow-designer/how-to-invoke-the-workflow-debugger.md)です。  
  
5.  コードがいずれかのブレークポイントまで実行されると、そのブレークポイントに関連付けられている XAML 要素が強調表示されます。 次のブレークポイントに移動するには、使用、 **F10**または**F11**キー。  
  
## <a name="see-also"></a>参照  
 [方法: ワークフロー内のブレークポイントを設定](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [ワークフロー デバッガーを呼び出す方法](../workflow-designer/how-to-invoke-the-workflow-debugger.md)