---
title: "ソース コントロール VSPackage を実装するかどうかを決定します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理パッケージのソース管理パッケージについて"
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# ソース コントロール VSPackage を実装するかどうかを決定します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ここでは選択のソース管理ソリューションのソース管理プラグインとソース管理の詳細についてはVSPackage し適切な統合のパスの選択のためのガイドラインを示します。  
  
## リソースを含むソリューションがソース管理  
 リソースがありソース管理パッケージを記述する際のオーバーヘッドを呼び出す場合はソース管理プラグイン API ベースのプラグインを作成できます。  これはソース管理パッケージを同時に使用することができます。ソース管理プラグインとパッケージの間でオン デマンド式で切り替えることができます。  詳細については、「[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)」を参照してください。  
  
## 豊富な機能セットを含むソリューションがソース管理  
 ソース管理プラグイン API を使用して取り込む充実したソース管理のモデルを提供するソース管理ソリューションを実行する場合統合のパスとしてソース管理パッケージを検討できます。  これは特に独自の方法とカスタムのソース管理のイベントを処理できるように \(ソース管理プラグインと通信したり基本のソース管理の UI を提供するソース管理のアダプターのパッケージに置き換える適用されます。  既にコンテンツのソース管理の UI がありその [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のエクスペリエンスを保持する場合ソース管理オプションではそのパッケージを行うことができます。  ソース管理パッケージは一般的に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE で使用するために特化されています。  
  
 ソース管理のロジックおよび UI を柔軟に豊富なコントロールを提供するソース管理ソリューションを実行する場合ソース管理の統合パッケージのルートが望ましい場合があります。  次の操作を行うことができます。  
  
1.  独自のソース管理 VSPackage を登録します。[登録と選択](../../extensibility/internals/registration-and-selection-source-control-vspackage.md) を参照してください。  
  
2.  カスタム UI と既定のソース コントロールの UI を置き換えます。[カスタム ユーザー インターフェイス](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)\(を参照\)。  
  
3.  使用するグリフを指定するにはソリューション エクスプローラーでグリフのイベントを処理します \([グリフ コントロール](../../extensibility/internals/glyph-control-source-control-vspackage.md) を参照してください。  
  
4.  ハンドルのクエリを編集してクエリを保存するイベント \([クエリを保存クエリの編集](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md) を参照してください。  
  
## 参照  
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)