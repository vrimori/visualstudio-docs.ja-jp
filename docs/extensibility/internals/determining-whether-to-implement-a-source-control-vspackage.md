---
title: ソース管理 VSPackage を実装するかどうかを決定する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab61171841e345004d097adc9645cc1aa73e74f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984796"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>ソース管理 VSPackage を実装するかどうかを決定します。
このセクションでは、適切な統合パスの選択について大まかなガイドラインをソリューションと、ソース管理を拡張するためソース管理プラグインとソース管理 Vspackage の選択を詳しく説明します。  
  
## <a name="small-source-control-solution-with-limited-resources"></a>限られたリソースで小さなソース制御ソリューション  
 リソースが限られているし、ソース管理パッケージの作成のオーバーヘッドに伴う負担することはできません、ソース管理プラグイン API ベースのプラグインを作成できます。これにより、ソース管理のパッケージと並行して動作して、ソース管理プラグインとオンデマンドのパッケージ間で切り替えることができます。 詳細については、次を参照してください。[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)します。  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>豊富な機能セットでの大規模なソース管理ソリューション  
 ソース管理プラグイン API を使用して適切にキャプチャされていないソースの豊富なコントロール モデルを提供するソース管理ソリューションを実装する場合は、統合パスとして、ソース管理パッケージを検討できます。 これは適用されます置換ではなく、ソース コントロール アダプター パッケージ (これはソース管理プラグインと通信し、基本ソース コントロールの UI を提供します) 場合に特にを独自ソース コントロールのイベントをカスタムの方法で処理できるようにします。 満足のいくソース UI を制御およびでは、そのエクスペリエンスを維持する必要があれば[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、ソース管理パッケージのオプションを使用して、それを実行できます。 ソース管理パッケージがジェネリックでないし、のみで使用するために設計されていますが[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE。  
  
 柔軟性とソース制御ロジックと UI の高度な制御を提供するソース管理ソリューションを実装する場合は、ソース管理パッケージ統合ルートしたい場合があります。 次の操作を行うことができます。  
  
1.  独自のソース管理 VSPackage の登録 (を参照してください[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md))。  
  
2.  既定のソース管理 UI に、カスタム UI を置き換えます (を参照してください[カスタム ユーザー インターフェイス](../../extensibility/internals/custom-user-interface-source-control-vspackage.md))。  
  
3.  使用して、ソリューション エクスプ ローラーのグリフのイベントを処理するグリフの指定 (を参照してください[グリフ コントロール](../../extensibility/internals/glyph-control-source-control-vspackage.md))。  
  
4.  クエリを編集し、クエリの保存のイベントを処理 (を参照してください[クエリ編集のクエリの保存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md))。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインを作成します。](../../extensibility/internals/creating-a-source-control-plug-in.md)