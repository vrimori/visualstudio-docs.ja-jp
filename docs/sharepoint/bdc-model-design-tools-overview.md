---
title: BDC モデルのデザイン ツールの概要 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c5a799a245d2149161809977446d0c005dbe293
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914503"
---
# <a name="bdc-model-design-tools-overview"></a>BDC モデルのデザイン ツールの概要
  ビジネス データ接続 (BDC) モデルを設計するには、BDC デザイナーを使用して、 **BDC メソッドの詳細**ウィンドウ、および**BDC エクスプ ローラー**。  
  
 **BDC エクスプ ローラー**モデルを参照して、モデルを検索および型記述子を定義することができます。  
  
## <a name="bdc-designer"></a>BDC デザイナー
 BDC デザイナーでは、モデルのエンティティを定義して、相互の関係を視覚的に整理できます。 次のタスクを実行するのにには、BDC デザイナーを使用します。  
  
- モデルにエンティティを追加します。  
  
- モデルからエンティティを削除します。  
  
- エンティティ間のリレーションシップを定義します。  
  
  BDC デザイナーを開くには、そのプロジェクトで、モデル ファイルをダブルクリックし、モデル ファイルのショートカット メニューを開くまたは選択し、**開く**します。 エンティティをドラッグまたはコピーして、モデルを追加する、**エンティティ**から、**ツールボックス**デザイナーにします。 2 つのエンティティ間のアソシエーションを作成するには、選択、**アソシエーション**を制御、**ツールボックス**を最初のエンティティを選択し、別のエンティティを選択します。  
  
## <a name="bdc-method-details-window"></a>BDC メソッドの詳細 ウィンドウ
 使用して、 **BDC メソッドの詳細**ウィンドウで、インスタンスのパラメーターを定義およびメソッドの記述子をフィルター処理します。  
  
 Finder、固有の検索、作成者、アップデーター、および Deleter メソッドをすばやく生成できます、 **BDC メソッドの詳細**ウィンドウ。 これらのメソッドを生成するときに、Visual Studio は、メソッドにパラメーター、インスタンス、および型の記述子などのメタデータを追加します。 特定のシナリオを満たすためにこのメタデータを変更できます。  
  
 開くには、 **BDC メソッドの詳細**ウィンドウ、メニュー バーで、選択**ビュー** > **その他の Windows** > **BDC メソッドの詳細**.  
  
 内のメソッドを表示する、 **BDC メソッドの詳細**ウィンドウで、BDC デザイナーでエンティティを選択します。 選択したエンティティのメソッドに表示、 **BDC メソッドの詳細**ウィンドウ。 BDC デザイナーでエンティティを選択しない場合、 **BDC メソッドの詳細**ウィンドウ情報は表示されません。  
  
 展開または折りたたみ内のノード、 **BDC メソッドの詳細**ウィンドウで、インスタンスのパラメーターを定義および記述子のフィルター処理します。 使用して、 **BDC エクスプ ローラー**型記述子を定義します。  
  
## <a name="bdc-explorer"></a>BDC エクスプローラー
 **BDC エクスプ ローラー**モデルを構成する要素が表示されます。 開くには、 **BDC エクスプ ローラー**、メニュー バーで、**ビュー** > **その他の Windows** > **BDC エクスプ ローラー**します。 モデルを参照するには、ノードを展開、 **BDC エクスプ ローラー**します。 各ノードでは、モデル ファイルの XML の要素を表します。  
  
 内のノードを選択すると、 **BDC エクスプ ローラー**、選択した各ノードのプロパティに表示されます、**プロパティ**ウィンドウ。 これらのプロパティの多くは、モデル ファイル内の属性に対応します。 上部にある検索ボックスを使用して、モデルを検索することができます、 **BDC エクスプ ローラー**します。  
  
> [!NOTE]  
>  **BDC エクスプ ローラー**識別子、カスタム プロパティ、ローカライズされた文字列、アソシエーションのグループ、アクション、フィルター記述子、アクションのコントロール リスト、および既定のパラメーター値は表示されません。  
  
### <a name="define-type-descriptors"></a>型記述子を定義します。
 使用して、 **BDC エクスプ ローラー**型記述子を定義します。 BDC エクスプ ローラーを使用すると、1 回型記述子を定義し、その後、モデルの他の場所では、その型記述子を再利用できます。 これを行うには、型記述子をコピーし、他のパラメーターに貼り付けることか記述子を入力します。  
  
> [!NOTE]  
>  元の型記述子への変更は、その型記述子のコピーには影響しません。  
  
 詳細については、次を参照してください。[方法: パラメーターの型記述子を定義](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)します。  
  
## <a name="see-also"></a>関連項目
 [方法: BDC モデルの作成](../sharepoint/how-to-create-a-bdc-model.md)   
 [方法: エンティティ モデルを追加します。](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [方法: Finder メソッドを追加](../sharepoint/how-to-add-a-finder-method.md)   
 [方法: 特定の Finder メソッドを追加](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [方法: Creator メソッドを追加](../sharepoint/how-to-add-a-creator-method.md)   
 [方法: Deleter メソッドを追加](../sharepoint/how-to-add-a-deleter-method.md)   
 [方法: Updater メソッドの追加](../sharepoint/how-to-add-an-updater-method.md)   
 [エンティティ間のアソシエーションを作成します。](../sharepoint/creating-an-association-between-entities.md)   
 [チュートリアル: sharepoint ビジネス データを使用して外部リストを作成します。](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [SharePoint ビジネス データを統合します。](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [ビジネス データ接続モデルの作成](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [ビジネス データ接続モデルの設計](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
 
