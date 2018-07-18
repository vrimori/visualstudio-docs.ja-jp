---
title: ソース コントロールの VSPackage を実装するかどうかを決定する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 203144e5b262c093204fe9eafa3a2a5db85eccb3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128878"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>ソース コントロールの VSPackage を実装するかどうかを決定します。
このセクションでは、適切な統合パスの選択方法の大まかなガイドラインをソリューションと、ソース管理を拡張するため、ソース管理プラグインとソース管理の Vspackage の選択を詳しく説明します。  
  
## <a name="small-source-control-solution-with-limited-resources"></a>限られたリソースで小さなソース制御ソリューション  
 リソースが限られているし、ソース管理パッケージを作成するオーバーヘッドに伴う負担することはできない場合、は、ソース管理プラグイン API ベースのプラグインを作成できます。これにより、ソース管理パッケージでは、サイド バイ サイドで操作して、ソース管理プラグインとオンデマンドのパッケージ間で切り替えることができます。 詳細については、次を参照してください。[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)です。  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>豊富な機能セットでの大規模なソース管理ソリューション  
 適切にキャプチャされていないソース コントロールのプラグイン API を使用して、豊富なソース制御モデルを提供するソース管理ソリューションを実装する場合は、統合パスとしてソース管理パッケージを検討する可能性があります。 これは適用されます (をソース管理プラグインと通信し、基本ソース コントロール UI を提供) ソース コントロール アダプターのパッケージを置換することではなく、場合に特に独自のカスタム形式でソース コントロールのイベントを処理できるようにします。 コントロール UI での経験があることを保持する満足のいくソースがあれば[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]パッケージのソース管理オプションでは、それを実行することができます。 ソース管理パッケージがジェネリックではありませんしで使用するためだけに設計されていますが[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE です。  
  
 柔軟性とソース制御ロジックと UI の高度な制御を提供するソース管理ソリューションを実装する場合は、ソース管理パッケージ統合ルートしたい場合があります。 次の操作を行うことができます。  
  
1.  独自のソース コントロールの VSPackage を登録 (を参照してください[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md))。  
  
2.  既定のソース管理 UI をカスタムの UI に置き換えます (を参照してください[カスタム ユーザー インターフェイス](../../extensibility/internals/custom-user-interface-source-control-vspackage.md))。  
  
3.  使用して、ソリューション エクスプ ローラーのグリフのイベントを処理するグリフを指定 (を参照してください[グリフ コントロール](../../extensibility/internals/glyph-control-source-control-vspackage.md))。  
  
4.  クエリを編集し、クエリの保存のイベントを処理 (を参照してください[クエリ編集のクエリの保存](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md))。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)