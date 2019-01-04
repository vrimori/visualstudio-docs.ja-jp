---
title: プロジェクト モデルの要素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee628d56094026b588c76451c143158000636a5c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962611"
---
# <a name="elements-of-a-project-model"></a>プロジェクト モデルの要素
インターフェイスと実装のすべてのプロジェクトの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]基本的な構造を共有: プロジェクトの種類のプロジェクト モデル。 VSPackage を開発するには、プロジェクト モデルを取得するでは、設計上の決定に従っているし、IDE によって提供されるグローバルの機能と連携するオブジェクトを作成します。 プロジェクト項目を保存する方法を制御する、たとえば、制御できない通知ファイルを維持する必要があります。 ユーザーが開いているプロジェクト項目にフォーカスが移るし、選択**保存**上、**ファイル**メニューで、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]メニュー バーで、プロジェクトの種類コードする必要があります、IDE からコマンドをインターセプト、ファイルを保持してとファイルが不要になった変更されたことを IDE に戻るには、通知を送信します。  
  
 VSPackage は、IDE インターフェイスへのアクセスを提供するサービスを介して、IDE と対話します。 たとえば、特定のサービスにするモニターとルート コマンドやプロジェクトで行った選択のコンテキスト情報を提供します。 VSPackage のために必要なすべてのグローバル IDE 機能は、サービスによって提供されます。 サービスの詳細については、次を参照してください。[方法。サービスを取得](../../extensibility/how-to-get-a-service.md)します。  
  
 その他の実装の考慮事項:  
  
- 1 つのプロジェクト モデルは、1 つ以上のプロジェクトの種類を含めることができます。  
  
- プロジェクトの種類とアテンダント プロジェクト ファクトリに登録されていない個別に Guid。  
  
- 各プロジェクト テンプレート ファイルまたはユーザーが経由で、新しいプロジェクトを作成するときに、新しいプロジェクト ファイルを初期化するためにウィザードが適用される場合があります、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI。 たとえば、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]テンプレートは、最終的になるものの .vcproj ファイルを初期化します。  
  
  次の図は、プライマリ インターフェイス、サービス、および一般的なプロジェクトの実装を構成するオブジェクトを示します。 アプリケーションのヘルパーを使用する`HierUtil7`、基になるオブジェクトとその他のプログラミングの定型コードを作成します。 詳細については、`HierUtil7`アプリケーションのヘルパーを参照してください[プロジェクトの種類 (C++) を実装するために使用 HierUtil7 プロジェクト クラス](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)します。  
  
  ![Visual Studio プロジェクト モデル グラフィック](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
  Project モデル  
  
  インターフェイスと、前の図に表示されるサービスと、ダイアグラムに含まれていないその他の省略可能なインターフェイスの詳細については、次を参照してください。[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)します。  
  
  プロジェクトのコマンドをサポートし、したがってを実装する必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンド コンテキスト Guid によるコマンドのルーティングに参加するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト:新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [HierUtil7 プロジェクト クラスを使用して、プロジェクトの種類 (C++) を実装するには](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)   
 [プロジェクト ファクトリを使用してプロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [方法: サービスを取得します。](../../extensibility/how-to-get-a-service.md)   
 [プロジェクトの種類を作成します。](../../extensibility/internals/creating-project-types.md)
