---
title: プロジェクトの種類の設計に関する決定事項 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c28c6f29454feed94407d6e37c3432247b9a4a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="project-type-design-decisions"></a>プロジェクトの種類の設計に関する決定事項
新しいプロジェクトの種類を作成する前に、プロジェクトの種類に関するいくつかの設計に関する決定を行う必要があります。 使用して、プロジェクトが含まれる項目、プロジェクト ファイルの保存方法、およびどのようなコミットメント モデルの種類を決定する必要があります。  
  
## <a name="project-items"></a>プロジェクト項目  
 プロジェクトでは、ファイルや抽象オブジェクトを使用しますか。 ファイルを使用する場合はそれらが参照に基づくか、ディレクトリ ベースのファイルか。 ローカルまたはリモートにするには、ファイルまたは抽象オブジェクトが行われていることとは  
  
 プロジェクト内の項目として使用できるは、ファイル、することもできますデータベース データのリポジトリまたは接続内のオブジェクトより抽象的オブジェクト、インターネットを経由します。 項目がファイルの場合は、プロジェクト参照に基づくまたはできますディレクトリ ベースのプロジェクトです。  
  
 プロジェクトでは参照に基づく、項目は、複数のプロジェクトに表示できます。 ただし、項目が表す実際のファイルは 1 つのディレクトリのみにあります。 ディレクトリ ベースのプロジェクトでは、ディレクトリ構造に存在するすべてのプロジェクト項目です。  
  
 ローカルの項目は、アプリケーションがインストールされている同じコンピューターに格納されます。 リモートの項目は、ローカル ネットワークでは、別のサーバーや他の場所は、インターネット上に格納できます。  
  
## <a name="project-file-persistence"></a>プロジェクト ファイルの永続化  
 システムでは一般的なフラット ファイル、または構造化ストレージに、データを格納するされますか。 標準のエディターまたはプロジェクト固有のエディターを使用してファイルを開きますか。  
  
 データを保持するためほとんどのアプリケーションは、データをファイルに保存し、ユーザーが確認する必要がありますまたは情報を変更するときに読むことです。  
  
 複合ファイルとも呼ばれます、構造化された記憶域は通常、いくつかのコンポーネント オブジェクト モデル (COM) オブジェクトが 1 つのファイルに保存されるデータを格納する必要がある場合に使用されます。 構造化された記憶域を持つ複数の異なるソフトウェア コンポーネントが 1 つのディスク ファイルを共有できます。  
  
 プロジェクト内の項目の持続性に関して考慮すべきいくつかのオプションがあります。 次のオプションのいずれかを実行できます。  
  
-   変更されると、各ファイルを個別に保存します。  
  
-   1 つの多くのトランザクションをキャプチャ**保存**操作します。  
  
-   ファイルをローカルに保存し、サーバーにパブリッシュまたはアイテムが、リモート オブジェクトへのデータ接続を表すときに、プロジェクト項目を保存するための別のアプローチを使用します。  
  
 永続化の詳細については、次を参照してください。[プロジェクトの永続化](../../extensibility/internals/project-persistence.md)と[開始タグとプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)です。  
  
## <a name="project-commitment-model"></a>プロジェクトのコミットメント モデル  
 永続化されたデータ オブジェクトが開かれるダイレクト モードまたはトランザクション モードにしますか?  
  
 データ オブジェクトが直接モードで開かれると、データに加えられた変更は、ユーザーが手動でファイルを保存するとき、またはすぐに反映されます。  
  
 トランザクション モードを使用してデータ オブジェクトが開かれると、変更はメモリに一時的な場所に保存され、ユーザーが手動でファイルを保存するよう選択するまではコミットされません。 その時点ですべての変更を同時に発生する必要があります。 または変更は行われません。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [開くと、プロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)   
 [プロジェクトの永続化](../../extensibility/internals/project-persistence.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)   
 [プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)   
 [プロジェクト タイプの作成](../../extensibility/internals/creating-project-types.md)