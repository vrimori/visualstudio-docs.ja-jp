---
title: "DSL ライブラリを使用して、Dsl の間でクラスの共有 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 935862ec8bbe79634595d547067204c9893a4944
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL ライブラリによる DSL 間でのクラスの共有
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK は、別の DSL にインポートすることができます不完全な DSL 定義を作成することができます。 これにより、類似したモデルの共通部分を考慮することができます。  
  
## <a name="creating-and-using-dsl-libraries"></a>作成して、DSL ライブラリを使用します。  
  
#### <a name="to-create-a-dsl-library"></a>DSL ライブラリを作成するには  
  
1.  新しい DSL プロジェクトを作成し、DSL ライブラリ ソリューション テンプレートを選択します。  
  
     DSL の単一のプロジェクトは、空のモデルで作成されます。  
  
2.  ドメイン クラス、リレーションシップ、図形に追加することができます。  
  
     ライブラリ内の要素は、1 つの埋め込みツリーを形成する必要はありません。  
  
     インポーターが使用できるリレーションシップを定義するのには、2 つのドメイン クラスを作成し、それらの間のリレーションシップを作成します。  
  
     設定を検討してください、**継承修飾子**ドメイン クラスの`Abstract`します。  
  
3.  接続ビルダーなどの DSL のエクスプ ローラーで定義する要素を追加することができます。  
  
4.  検証制約など、追加のコードを必要とするカスタマイズを追加することができます。  
  
5.  をクリックして**すべてのテンプレートを変換**です。  
  
6.  プロジェクトをビルドします。  
  
7.  DSL を使用するには、他のユーザーを配布するときに、コンパイルされたアセンブリ (DLL) とファイルの両方を指定する必要があります`DslDefinition.dsl`です。 下のフォルダーにコンパイルされたアセンブリを見つけることができます。`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>DSL ライブラリをインポートするには  
  
1.  別の DSL 定義内で**DSL のエクスプ ローラー**、DSL のルート クラスを右クリックし、クリックして**新しい DslLibrary インポートの追加**。  
  
2.  [プロパティ] ウィンドウで、設定、**ファイル パス**ライブラリのです。 相対パスまたは絶対パスのいずれかを使用することができます。  
  
     インポートされたライブラリは、読み取り専用モードには、DSL のエクスプ ローラーで表示されます。  
  
3.  インポートされたクラスは、基本クラスとして使用できます。 インポートの DSL のドメイン クラスを作成し、プロパティ ウィンドウで、設定**基本クラスの**をインポートするクラス。  
  
4.  すべてのテンプレートの変換 をクリックします。  
  
5.  DSL プロジェクトに、DSL ライブラリ プロジェクトによってビルドされたアセンブリ (DLL) への参照を追加します。  
  
6.  ソリューションをビルドします。  
  
 DSL ライブラリは、その他のライブラリをインポートできます。 ライブラリをインポートすると、そのインポートも自動的に DSL のエクスプ ローラーに表示されます。  
  
## <a name="see-also"></a>参照  
 [方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
