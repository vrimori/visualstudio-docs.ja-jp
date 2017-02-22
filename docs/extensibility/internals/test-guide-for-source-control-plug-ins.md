---
title: "ソース管理プラグインのテストのガイド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プラグインをソース管理"
  - "プラグインをテストするソース管理 [Visual Studio SDK]"
  - "テストでは、ソース管理プラグイン"
  - "テスト、ソース管理プラグインを"
  - "ソース管理プラグインをテスト ガイド"
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース管理プラグインのテストのガイド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ここでは [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をソース管理プラグインをテストするための指針を示します。  一般的なテスト区分の広範な概要問題となる可能性のある複雑な領域の一部が用意されています。  この概要はテスト ケースのすべて網羅したものであるためのものではありません。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の最新の IDE にあるバグの修正と機能強化を見つけられなかった前にソース管理プラグインに問題が見つかる場合があります [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の以前のバージョンを使用しているとき。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の以前のバージョンからプラグインが変更されたいなくても列挙した領域にはこのセクションの既存のソース管理プラグインをテストすることを強くお勧めします。  
  
## 共通の準備  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] コンピューターとインストール対象のソース管理プラグインが必要です。  同様に設定される 2 番目のコンピューターはソース管理からテストが開きますの一部に使用できます。  
  
## 用語の定義  
 このテストのガイドで次の用語の定義を使用するには :  
  
 クライアント プロジェクト  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のプロジェクトの種類で使用できるソース管理の統合をサポートする \([!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)][!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]または [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]\)。  
  
 Web プロジェクト  
 Web プロジェクトには 4 種類あります : ファイル システムローカル IIS サイトとリモート サイトFTP。  
  
-   ローカル パスにファイル システムのプロジェクトは作成されますがUNC パスでインストールされるように \(IIS\) 内部的にアクセス要求せずソース管理下に IDE 内からクライアント プロジェクトと同じように配置するときにインターネット インフォメーション サービス \(IIS\) が。  
  
-   同じコンピューターにインストールされローカル コンピューターを指す URL でアクセスできる IIS のローカルの IIS プロジェクトで動作します。  
  
-   リモート サイト プロジェクトはIIS のサービスの下に作成されますがIIS サーバー コンピューターに存在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 内からソース管理下に配置されます。  
  
-   FTP のプロジェクトによってFTP サーバーがありソース管理下に置くことはできません。  
  
 登録  
 ソリューションの用語またはソース管理プロジェクト。  
  
 ストア バージョン  
 ソース管理プラグイン API を使用してアクセス ソース管理データベース。  
  
## このセクションで説明されているテスト区分  
  
-   [テスト領域 1: ソース管理から開く\/を追加します。](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   1a 場合 : ソリューションをソース管理に追加  
  
    -   1b 場合 : ソース管理からソリューションを開く  
  
    -   1c 場合 : ソース管理からソリューションの追加  
  
-   [ソース管理からのテスト領域 2: Get](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [テスト領域 3: チェック アウト\]、\[チェック アウトを元に戻す](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   ケース 3: チェック アウトと元のチェック アウト  
  
    -   3a 場合 : チェックアウト  
  
    -   3b 場合 : 切断されたチェック アウト  
  
    -   3c 場合 : クエリおよびクエリの編集の保存 \(QEQS\)  
  
    -   3D 場合 : サイレント チェック アウト  
  
    -   ケース 3e: チェックアウトの取り消し  
  
-   [テスト領域 4: で確認してください。](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   4a 場合 : 変更された項目  
  
    -   フィルター場合 : ファイルの追加  
  
    -   : した場合プロジェクトの追加  
  
-   [テスト領域 5: ソース管理の変更](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   5a 場合 : バインド  
  
    -   5b 場合 : バインドの解除  
  
    -   5c 場合 : 再バインドされます  
  
-   [テスト領域 6: 削除](../../extensibility/internals/test-area-6-delete.md)  
  
-   [テスト領域 7: 共有](../../extensibility/internals/test-area-7-share.md)  
  
-   [テスト領域 8: プラグインの切り替え](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   ケース 8a: 自動変更  
  
    -   ケース 8b: ソリューション ベースの変更  
  
## 参照  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)