---
title: プロファイルとステレオタイプを使用したモデルのカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2dd494b475b5d9068597857a2f4df12e5fed8e2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537414"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>プロファイルとステレオタイプを使用したモデルのカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロファイルとステレオタイプを使用してモデルをカスタマイズ](https://docs.microsoft.com/visualstudio/modeling/customize-your-model-with-profiles-and-stereotypes)します。  
  
Visual Studio では、クラスやコンポーネントなどの標準の UML モデル要素を特定の目的に合わせてカスタマイズできます。 適用することができます、*ステレオタイプ*要素のプロパティの一覧を変更できるモデル要素にします。 ステレオタイプと呼ばれるコレクション内で定義された*プロファイル*します。  
  
 この機能をサポートする Visual Studio のバージョンを確認するには、「 [アーキテクチャ ツールとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  
  
 ステレオタイプを使用するには、パッケージをプロファイルにリンクします。 これにより、プロファイルで定義されているステレオタイプをパッケージ内の要素に適用できます。 Visual Studio をインストールするときに、いくつかのプロファイルもインストールされます。 また、独自のプロファイルを定義できます。  
  
 ステレオタイプは、要素のプロパティ リストで設定できます。 次の例に示すように、図のシェイプの主な種類については、適用されたステレオタイプもシェイプに表示されます。  
  
 ![ステレオタイプで UML クラスです。](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")  
  
> [!NOTE]
>  プロファイルを使用してモデルを生成し、そのモデルを他のユーザーと共有する場合、それぞれのコンピューターに同じプロファイルをインストールしなければ、ステレオタイプを表示できません。  
  
## <a name="related-topics"></a>関連トピック  
  
|Title|説明|  
|-----------|-----------------|  
|[UML モデル要素にステレオタイプを追加する](../modeling/add-stereotypes-to-uml-model-elements.md)|モデル要素をパッケージ内に配置して、パッケージをプロファイルにリンクし、ステレオタイプを要素に適用します。|  
|[UML モデルの標準ステレオタイプ](../modeling/standard-stereotypes-for-uml-models.md)|Visual Studio をインストールするときに、UML 標準プロファイル L2 および L3 がインストールされます。既定では、すべてのモデルがこれらのプロファイルにリンクされます。 これらのプロファイルによって、モデルに注釈を付けるために使用できるステレオタイプが提供されます。<br /><br /> たとえば、«specification» ステレオタイプをクラスに適用して、クラスの使用目的が、そのインスタンスの外部から見える動作の定義のみであることを示すことができます。|  
|[プロファイルを定義して UML を拡張する](../modeling/define-a-profile-to-extend-uml.md)|独自のアプリケーション領域に適合した独自のステレオタイプとツールを定義できます。<br /><br /> たとえば、銀行業務ソフトウェアを開発する場合、クラスに適用できる «Account» ステレオタイプを定義できます。 これにより、クラス図を使用して複数の異なる種類の口座および口座間のリレーションシップを記述できます。|  
|[UML プロファイルのインストール](../modeling/install-a-uml-profile.md)|他のユーザーから UML プロファイルを受け取った場合、それを自分のコンピューターにインストールできます。|  
|[カスタム モデリング ツールボックス アイテムを定義する](../modeling/define-a-custom-modeling-toolbox-item.md)|カスタム ツールボックス項目を使用すると、新しい要素にステレオタイプを繰り返し設定する手間を省くことができます。|  
|[ステレオタイプにより UML クラスの色](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|このサンプル コードは、UML 図を拡張します。 要素のステレオタイプに従って、UML シェイプの色を自動的に設定します。|



