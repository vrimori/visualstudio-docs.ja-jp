---
title: "BDC モデルのデザイン ツールの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
ms.assetid: dbd7b746-9e93-4ed4-a546-4a6f17a4725f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eaf6871f7ad9316ba2dbdaa8fa29b4810b1d6a3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="bdc-model-design-tools-overview"></a>BDC モデルのデザイン ツールの概要
  BDC デザイナーを使用してビジネス データ接続 (BDC) モデルを設計することができます、 **BDC メソッドの詳細**ウィンドウ、および**BDC エクスプ ローラー**です。  
  
 **BDC エクスプ ローラー**モデルの参照し、モデルを検索、型記述子を定義することができます。  
  
## <a name="bdc-designer"></a>BDC デザイナー  
 BDC デザイナーでは、モデルのエンティティを定義して、相互の関係を視覚的に整理できます。 次のタスクを実行するのに BDC デザイナーを使用します。  
  
-   モデルにエンティティを追加します。  
  
-   モデルからエンティティを削除します。  
  
-   エンティティ間のリレーションシップを定義します。  
  
 BDC デザイナーを開くには、そのプロジェクトで、モデル ファイルをダブルクリックし、モデル ファイルのショートカット メニューを開くまたはを選択し、**開く**です。 エンティティ モデルを追加、ドラッグまたはコピーして、**エンティティ**から、**ツールボックス**デザイナーにします。 2 つのエンティティ間の関連付けを作成するには、選択、**アソシエーション**で制御、**ツールボックス**を最初のエンティティを選択して、2 番目のエンティティを選択します。  
  
## <a name="bdc-method-details-window"></a>BDC メソッドの詳細 ウィンドウ  
 使用して、 **BDC メソッドの詳細**パラメーターのインスタンスを定義して、メソッドの記述子をフィルター処理するウィンドウです。  
  
 Finder、固有の検索、作成者、アップデーター、および削除子のメソッドをすばやく生成することができます、 **BDC メソッドの詳細**ウィンドウです。 これらのメソッドを生成するときに、Visual Studio は、メソッドにパラメーター、インスタンス、および型記述子などのメタデータを追加します。 特定のシナリオを満たすためには、このメタデータを変更することができます。  
  
 開くには、 **BDC メソッドの詳細**ウィンドウ、メニュー バーを選択して**ビュー**、**その他のウィンドウ**、 **BDC メソッドの詳細**です。  
  
 内のメソッドを表示する、 **BDC メソッドの詳細**ウィンドウで、BDC デザイナーで、エンティティを選択します。 選択したエンティティのメソッドに表示、 **BDC メソッドの詳細**ウィンドウです。 BDC デザイナーにエンティティを選択しない場合、 **BDC メソッドの詳細**ウィンドウに情報が表示されません。  
  
 展開または折りたたみの内のノード、 **BDC メソッドの詳細**インスタンス、パラメーターを定義して記述子をフィルター処理するウィンドウです。 使用して、 **BDC エクスプ ローラー**型記述子を定義します。  
  
## <a name="bdc-explorer"></a>BDC エクスプローラー  
 **BDC エクスプ ローラー**モデルを構成する要素が表示されます。 開くには、 **BDC エクスプ ローラー**、メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、 **BDC エクスプ ローラー**です。 モデルを参照するときにノードを展開、 **BDC エクスプ ローラー**です。 各ノードは、モデル ファイルの XML の要素を表します。  
  
 内のノードを選択すると、 **BDC エクスプ ローラー**、選択した各ノードのプロパティに表示されます、**プロパティ**ウィンドウです。 これらのプロパティの多くは、モデル ファイル内の属性に対応します。 上部にある検索ボックスを使用して、モデルを検索することができます、 **BDC エクスプ ローラー**です。  
  
> [!NOTE]  
>  **BDC エクスプ ローラー**識別子、カスタム プロパティをローカライズされた文字列、関連付けグループ、アクション、フィルター記述子、アクションのコントロール リスト、および既定のパラメーター値は表示されません。  
  
### <a name="defining-type-descriptors"></a>型記述子を定義します。  
 使用して、 **BDC エクスプ ローラー**型記述子を定義します。 BDC エクスプ ローラーを使用すると、1 回、型記述子を定義し、モデルの他の場所には、その型記述子を再利用できます。 これを実現するには、型記述子をコピーし、その他のパラメーターに貼り付けるか記述子を入力します。  
  
> [!NOTE]  
>  元の型記述子への変更は、その型記述子のコピーには影響しません。  
  
 詳細については、次を参照してください。[する方法: パラメーターの型記述子を定義する](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: BDC モデルを作成](../sharepoint/how-to-create-a-bdc-model.md)   
 [方法: エンティティをモデルに追加します。](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: Specificfinder メソッドを追加します。](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドを追加](../sharepoint/how-to-add-an-updater-method.md)   
 [エンティティ間の関連付けを作成します。](../sharepoint/creating-an-association-between-entities.md)   
 [チュートリアル: sharepoint ビジネス データを使用して外部リストを作成します。](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [SharePoint にビジネス データの統合](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [ビジネス データ接続モデルを作成します。](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Business Data Connectivity モデルのデザイン](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  