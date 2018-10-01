---
title: '警告: 依存関係&#39;ファイル&#39;プロジェクトで&#39;プロジェクト&#39;の参照を上書きするために、実行ディレクトリにコピーできません&#39;ファイル。&#39; |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_warning
ms.assetid: 116819f3-a4d4-48b5-9e71-7c54660d38ef
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 7ea168095d67bb71d7aea9a1139a6df1956d14fb
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "47592495"
---
# <a name="warning-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-overwrite-the-reference-39file39"></a>警告: 依存関係&#39;ファイル&#39;プロジェクトで&#39;プロジェクト&#39;の参照を上書きするために、実行ディレクトリにコピーできません&#39;ファイル。&#39;
依存関係間で競合が発生しています。同じ名前の複数の異なるアセンブリ ファイルを、アプリケーションを実行する bin ディレクトリにコピーする必要があります。 依存関係の 1 つがプライマリ参照であるため、実行ディレクトリは競合を解決することができます。  
  
 このタスク一覧項目をダブルクリックすると、競合しているプライマリ参照ノードに移動します。  
  
 この警告は、存在する依存関係の競合を回避するために、競合している依存関係のいずれかを参照として追加している場合に発生します。 または、バージョン 1 の参照があるときに 2 番目の参照を追加して、そこで 1 番目の参照のバージョン 2 を参照している場合にも発生します。  
  
 ソリューションにプロジェクトが、相互への参照、参照は、ファイル参照として作成されたため、このエラーが発生します (を使用して、**参照**ボタン、[参照の追加](http://msdn.microsoft.com/en-us/2feb0fe2-0805-4cc9-8cba-b0315849dfb7)ダイアログボックス)、プロジェクト間参照ではなく (を使用して、**プロジェクト** タブで、**参照の追加** ダイアログ ボックス)。 プロジェクト間参照の利点は、ビルド システム内のプロジェクト間に依存関係が作成されることです。したがって、参照元のプロジェクトの前回のビルド以降に依存プロジェクトが変更されていると、依存プロジェクトのビルドが行われます。 ファイル参照ではビルド依存関係が作成されないため、依存プロジェクトをビルドせずに参照元のプロジェクトをビルドできます。したがって、参照が古くなる可能性があります。つまり、プロジェクトから、同じプロジェクトの以前にビルドされたバージョンが参照される場合があります。 その結果、bin ディレクトリ内に 1 つの DLL の複数のバージョンが求められる場合があります。これを実現するのは不可能なため、このエラー メッセージが出力されます。  
  
 このメッセージは、bin ディレクトリに競合があり、アプリケーションが正常に動作しない可能性があるときに常に表示されます。 この警告は、この問題を回避する操作を行っている場合でも表示されます。依存関係のバージョンがすべてのコンポーネントで正常に動作するかどうかをプロジェクト システムが判定できないためです。  
  
 **このエラーを修正するには**  
  
-   1 つ (または 0 個) のアセンブリ ファイルを bin ディレクトリにコピーします。そのためには、アセンブリ ファイルをグローバル アセンブリ キャッシュに配置します。 グローバル アセンブリ キャッシュにより、ファイル名の競合が解決します。 共通言語ランタイムはグローバル アセンブリ キャッシュ内のアセンブリを見つける方法を認識しているため、アセンブリのローカル コピーは作成されません。 詳細については、次を参照してください[アセンブリとグローバル アセンブリ キャッシュ](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433)と[エラー: 依存関係と競合するための依存関係 'file' プロジェクト 'project' では、実行ディレクトリにコピーできません '。ファイル '](../misc/error-the-dependency-file-in-project-project-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-file.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)   
 [グローバル アセンブリ キャッシュ](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [方法 : プロジェクトの依存関係を作成および削除する](../ide/how-to-create-and-remove-project-dependencies.md)