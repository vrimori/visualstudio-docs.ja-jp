---
title: Visual Studio の機能の Guid をパッケージ化 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C package GUIDs
ms.assetid: f56f0356-f3ac-48bc-9674-94259e29a4df
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ccac7110c5be5fcb0a7f846ca2756ecc334d767
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233288"
---
# <a name="package-guids-of-visual-studio-features"></a>Visual Studio の機能のパッケージ Guid
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

分離シェル アプリケーションの .pkgundef ファイルで次の Guid を使用するには、アプリケーションから特定のパッケージを除外します。  
  
## <a name="package-guids"></a>パッケージの Guid  
  
|機能分野|生のパッケージ名|パッケージ GUID|  
|------------------|----------------------|------------------|  
|コア IDE|パッケージを元に戻す|{1D76B2E0-F11B-11D2-AFC3-00105A9991EF}|  
||Visual Studio 環境のパッケージ|{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}|  
||Visual Studio のコマンド定義パッケージ|{44E07B02-29A5-11D3-B882-00C04F79F802}|  
||Visual Studio のディレクトリ一覧パッケージ|{5010C52F-44AB-4051-8CE1-D36C20D989B4}|  
||Visual Studio の一般的な IDE パッケージ|{6E87CFAD-6C05-4ADF-9CD7-3B7943875B7C}|  
||Visual Studio 環境のメニュー パッケージ|{715F10EB-9E99-11D2-BFC2-00C04F990235}|  
||Visual Studio は COM + ライブラリ マネージャー パッケージ|{ED8979BC-B02F-4dA9-A667-D3256C36220A}|  
||Visual Studio のソース管理の統合パッケージ|{53544C4D-E3F8-4AA0-8195-8A8D16019423}|  
||Visual Studio ソリューションのビルド パッケージ|{282BD676-8B5B-11D0-8A34-00A0C91E2ACD}|  
||テキスト管理パッケージ|{F5e7e720-1401-11d1-883b-0000f87579d2}|  
||Visual Studio VsSettings パッケージ|{F74C5077-D848-4630-80C9-B00E68A1CA0C}|  
|ヘルプ|Visual Studio ヘルプ パッケージ|{4A791146-19E4-11D3-B86B-00C04F79F802}|  
|タスク一覧、エラー一覧|ErrorListPackage|{4A9B7E50-AA16-11D0-A8C5-00A0C921A4D2}|  
|クラスのアウトライン|クラスのアウトライン パッケージ|{21AF45B0 FFA5-11 D 0-G63F-00A0C922E851}|  
|ツールボックス コントロール インストーラー|ツールボックス コントロール インストーラー パッケージ|{2C298B35-07DA-45F1-96A3-BE55D91C8d7A}|  
|Web プロジェクト|Microsoft.VisualStudio.Web|{349C5850-65DF-11DA-9384-00065B846F21}|  
||Visual Web Developer のプロジェクト システムのパッケージ|{39C9C826-8EF8-4079-8C95-428F5B1C323F}|  
||Visual Web Developer のプロジェクトの永続化パッケージ|{8FF02D1A-C177-4AC8-A62F-88FC6EA65F57}|  
||Visual Web Developer Web 移行パッケージ|{C1DAB116-2D63-493A-B970-10D7DD0B476E}|  
||Visual Web Developer Web パッケージ|{E7f851C8-6267-4794-B0FE-7BCAB6DACBB4}|  
||Visual Web Developer Web|{DC7F691A-91FC-4F7B-923E-FE829C3A18DC}|  
|HTML エディター|Visual Studio HTM エディター パッケージ|{1B437D20-F8FE-11D2-A6AE-00104BCC7269}|  
||Visual Web Developer の HTML ソース エディター パッケージ|{BFCC0C3C-6F87-4285-A6C8-BB616061800D}|  
|CSS エディター|Visual Studio CSS の パッケージの編集|{A764E895-518D-11d2-9A89-00C04F79EFC3}|  
|XML エディター|Visual Studio XML エディター パッケージ|{87569308-4813-40A0-9CD0-D7A30838CA3F}|  
|Web ブラウザー|Visual Studio の Web ブラウザーのパッケージ|{E8B06F41-6D01-11D2-AA7D-00C04F990343}|  
||Web アプリケーション プロジェクト ファクトリ、ブラウザーの機能の表示|{349C5851-65DF-11DA-9384-00065B846F21}|  
|バイナリ エディター|Visual Studio バイナリ エディター パッケージ|{5B98C2C0-CD7B-11D0-92DF-00A0C9138C45}|  
|Windows フォーム デザイナー|Windows フォーム デザイナーのホスト パッケージ|{68939055-38E0-4D17-92CB-8909710D8178}|  
||Windows フォーム デザイナー パッケージ|{7494682B-37A0-11D2-A273-00C04F8EF4FF}|  
||Windows フォーム デザイナーのリソース パッケージ|{7B5D447B-0B12-41EA-A84E-C822034422D4}|  
||Windows フォーム アプリケーションの構成パッケージ|{80C7728B-70A6-4528-8669-73E02D1B9C41}|  
||ElementHost デザイナー パッケージ|{7EAB3C71-59FF-4571-A5F3-643F255FC2E6}|  
|デバッガーの UI|Visual Studio Debugger|{C9DD4A57-47FB-11D2-83E7-00C04F9902C1}|  
|データベース ツール|Visual Database Tools のパッケージ|{220A4C17-7E7C-4663-BBCC-5E607C6543CD}|  
||Visual Studio のデータベース ツール デザイナー|{EF828E39-70F5-4b8e-A3A0-4C0ECD28A69A}|  
||Visual Studio データ デザイナー|{D6C919AA-1217-41E2-a13B-9B92E1866305}|  
||Visual Studio データ パッケージ|{E1AA7737-69BE-43d0-A425-E3097651E192}|  
||Visual Studio データ デザイナー機能拡張のパッケージ|{A8F602E2-40CE-4dAF-AE82-A457A91728B9}|  
||Visual Studio のエクスプ ローラーおよびデザイナー パッケージ|{8D8529D3-625D-4496-8354-3DAD630ECC1B}|  
||Microsoft レポート デザイナー|{F3A96850-E2AE-4E00-9278-8FE23F225A0D}|  
|DSL ランタイム|CommonModelingPackage|{D1091694-EA72-4BDD-8918-78324CC25448}|  
||Microsoft.VisualStudio.TextTemplating|{A9696DE6-E209-414D-BBEC-A0506fb0E924}|  
|SourceSafe のサポート|Visual SourceSafe プロバイダー パッケージ|{AA8EB8CD-7A51-11D0-92C3-00A0C9138C45}|  
||Visual SourceSafe プロバイダー スタブ パッケージ|{53544C4D-B03D-4209-A7D0-D9DD13A4019B}|  
|WPF デザイナー|WPFFlavor.WPFPackage|{B3BAE735-386C-4030-8329-EF48EEDA4036}|  
||XamlDesignerPackage|{512be089-83ec-4cc6-8483-cf16565ae209}|  
||XamlLanguagePackage|{2ef1ec52-c8bf-4fe0-8ece-ba9c0d5d1603}|  
||XamlDiagnosticsPackage|{8291c340-36b8-4c91-8c40-cce75398ff75}|  
|コード スニペット|Visual Studio のコード スニペットのパッケージ|{0B680757-2C29-4531-80FA-535A5178AA98}|  
|マネージ言語のプロジェクトのサポート|Visual Studio コンポーネントの列挙子|{588205E0-66e0-11D3-8600-00C04F6123B3}|  
||Visual Studio の設定とプロジェクト デザイナー パッケージ|{67909B06-91E9-4F3E-AB50-495046BE9A9A}|  
|テンプレートをエクスポートしてください.|テンプレート パッケージをエクスポートします。|{F1E4CFCA-4573-4345-8718-7BDE2b1F0BE8}|  
  
 その他の多くの機能に対して依存関係を実行するため、一部のパッケージを削除しません。 たとえば、"コア IDE"の下に表示されているを削除しない必要があります。  
  
 一部の機能を完全に削除することはできません。 たとえば、パッケージを削除する登録を解除することはありません**クラス ビュー**とその関連付けられたメニューのオプション、およびサービス。 **クラス ビュー**ウィンドウは、その他のキーの IDE 機能も提供します Visual Studio 環境パッケージによって提供されます。 削除する場合は**クラス ビュー**、削除する必要がありますも**検索し、置換**、環境**オプション**、ページ、**コマンド ウィンドウ**、および**出力**ウィンドウ。

