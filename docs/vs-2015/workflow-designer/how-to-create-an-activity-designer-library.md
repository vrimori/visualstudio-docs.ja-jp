---
title: '方法: アクティビティ デザイナー ライブラリを作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6802f92f349d15d48935f4e7c3db85abf7c12535
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258272"
---
# <a name="how-to-create-an-activity-designer-library"></a>アクティビティ デザイナー ライブラリを作成する方法
カスタム アクティビティ デザイナーを使用して、標準アクティビティやカスタム アクティビティのためのユーザー インターフェイスを作成できます。 ユーザー インターフェイスが複雑にならないようにして、1 つのアクティビティに対応するアクティビティ デザイナーを複数作成することができます。 このシナリオでは、複数の対象に対応したデザイナーを作成できます。  
  
### <a name="to-create-an-activity-designer-library"></a>アクティビティ デザイナー ライブラリを作成するには  
  
1.  [!INCLUDE[vs2010](../includes/vs2010-md.md)] を起動します。  
  
2.  **ファイル**メニューで、**新規**、し、**プロジェクト.** 開く、**新しいプロジェクト** ダイアログ ボックス。  
  
3.  **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#** または**Visual Basic**希望に応じてグループ化言語。  
  
4.  **テンプレート**ペインで、**アクティビティ デザイナー ライブラリ**します。  
  
5.  **名前**ボックスに、簡単に特定できるように、プロジェクトのわかりやすい名前を入力します。  
  
6.  **場所**ボックスに、プロジェクトを保存またはをクリックするディレクトリを入力**参照**それに移動します。  
  
7.  **ソリューション**ボックスに、ソリューションでは、わかりやすい名前を入力し、をクリックして**OK**します。  
  
    > [!NOTE]
    >  既存のソリューションのワークフロー コンソール アプリケーションを追加する場合は、そのソリューションを開きます[!INCLUDE[vs2010](../includes/vs2010-md.md)]でソリューションを右クリックして**ソリューション エクスプ ローラー**を選択し、**追加**、し**新しいプロジェクト.** 開く、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。  
  
8.  プロジェクト テンプレートにより、アクティビティ デザイナー定義が XAML で作成され、ソース コード内に分離コード実装ファイルが作成されます。 [!INCLUDE[wfd1](../includes/wfd1-md.md)]で、アクティビティ デザイナー用のキャンバスが開かれて表示されます。  
  
9. ドラッグ[!INCLUDE[avalon1](../includes/avalon1-md.md)]コントロールを**ツールボックス**カスタム アクティビティ デザイナーで使用するデザイン サーフェイスにします。  カスタム アクティビティ デザイナーを実装する方法の例は、次を参照してください。[方法: カスタム アクティビティ デザイナーを作成](http://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31)です。  
  
    > [!WARNING]
    >  カスタム アクティビティも既定のカスタム アクティビティ デザイナーを使用できる[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]アクティビティ。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)