---
title: プロジェクト モデルの要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4933e73df93c1f8a3bcf62e03b6883c0096f1d8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="elements-of-a-project-model"></a>プロジェクト モデルの要素
インターフェイスおよび実装内のすべてのプロジェクトの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]基本的な構造を共有: プロジェクトの種類のプロジェクトのモデル。 VSPackage を開発するには、プロジェクト モデルでは、IDE によって提供されるグローバルの機能と共に動作および設計に関する決定に準拠したオブジェクトを作成します。 プロジェクト項目を保存する方法を制御するなどが制御できない通知ファイルを永続化する必要があります。 ユーザーが開いているプロジェクト アイテムにフォーカスが移ります、選択**を保存**で、**ファイル**メニューで、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]メニュー バーで、プロジェクトの種類のコードする必要があります IDE からコマンドを途中受信、ファイルを保持してとファイルが不要になった変更されたことを IDE に戻るには、通知を送信します。  
  
 VSPackage は、IDE インターフェイスへのアクセスを提供するサービスを通した IDE と対話します。 たとえば、特定のサービスをモニターおよびルート コマンドしてプロジェクトで行った選択のコンテキスト情報を提供します。 VSPackage の必要なすべてのグローバル IDE 機能は、サービスによって提供されます。 サービスの詳細については、次を参照してください。[する方法: サービスを取得](../../extensibility/how-to-get-a-service.md)です。  
  
 その他の実装の考慮事項:  
  
-   1 つのプロジェクト モデルは、1 つ以上のプロジェクトの種類を含めることができます。  
  
-   プロジェクトの種類とアテンダント プロジェクト ファクトリに登録されていない個別に Guid。  
  
-   各プロジェクト テンプレートのファイルまたはユーザーが経由で、新しいプロジェクトを作成するときに、新しいプロジェクト ファイルを初期化するためにウィザードが適用される場合があります、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI。 たとえば、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]テンプレートが .vcproj ファイルを最終的になる新機能を初期化します。  
  
 次の図は、主なインターフェイスで、サービス、および一般的なプロジェクトの実装を構成するオブジェクトを示します。 基になるオブジェクトとその他のプログラミングの定型句を作成するのに、アプリケーション ヘルパーに渡し、HierUtil7 を使用することができます。 HierUtil7 アプリケーション ヘルパーの詳細については、次を参照してください。[ビルド内にありません: プロジェクトの種類 (C++) を実装する HierUtil7 プロジェクト クラスを使用して](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)です。  
  
 ![Visual Studio プロジェクト モデル グラフィック](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
Project モデル  
  
 詳細については、前の図に表示されるサービスとダイアグラムに含まれていない他の省略可能なインターフェイスのインターフェイスと、次を参照してください。[プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)です。  
  
 プロジェクトは、コマンドをサポートし、したがってを実装する必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>コマンドがコマンド コンテキストの Guid をルーティングに参加するインターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [ビルド内にありません: HierUtil7 プロジェクト クラスを使用して、プロジェクトの種類 (C++) を実装するには](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)   
 [プロジェクトのファクトリを使用してプロジェクトのインスタンスを作成します。](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [方法: サービスを取得](../../extensibility/how-to-get-a-service.md)   
 [プロジェクト タイプの作成](../../extensibility/internals/creating-project-types.md)