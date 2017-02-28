---
title: "PTVS の概要: コーディングの開始 (プロジェクト) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 6
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 96f7bc59b84e837b5a01eec0224171571491a7b1
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>PTVS の概要: コーディングの開始 (プロジェクト)
Python Tools for Visual Studio (PTVS) を使用すると、コードを管理できます。 
 
 これらの手順は、非常に短い [youtube ビデオ](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)で視聴できます。 
 
 以前に Python を使用したことがあれば分かるとおり、プロジェクトはディスク上でのファイルのレイアウト方法で定義されます。 これは通常の Python プロジェクトでは便利ですが、ファイルの数が多い場合 (JavaScript のある Web ページ、単体テスト、ビルド スクリプト)、ファイル システムが制約となってきます。 Visual Studio は、プロジェクトを使用して&3; つの事柄を達成します。 
 
- 重要なファイルを特定します。 重要なファイルは、バージョン管理システム (ソース ファイル、リソースなど) にチェックインするファイルです。ただし、ビルド出力として生成されるファイルは除きます。 また、他のユーザーがアプリで作業できるように別のコンピューターにコピーするファイルも、重要なファイルです。 
 
- ファイルを使用する方法を指定します。 変更されるたびにツールで処理する必要があるような、いくつかのファイルが存在することがあります。 Visual Studio プロジェクトは、この情報をキャプチャできます。 
 
- コンポーネントの境界を定義します。 アプリに複数のコンポーネントがある場合は、それぞれを別のプロジェクトに含めることができます。 これらは最終的に、別のビルドやデバッグ設定で構築された別のサーバーに展開される場合があります。または、C++ や Node.js など Visual Studio でサポートされている別の言語を使用して記述されることさえあります。 
 
 作業を開始するために役立つ、いくつかのプロジェクト テンプレートがあります。 作業する Python コードが既にある場合、From Existing code ウィザードは、すべてのファイルを含むプロジェクトを作成するために役立ちます。 いくつかの一般的なフレームワーク用に、複数の Web プロジェクトがあります。 PTVS サンプル パックでは、さらに多くのテンプレートが使用可能です。 指定された web テンプレートを他のフレームワークで使用できるようにするためのオプションがあります。 Python アプリケーション テンプレートは、クリーンな空のプロジェクトです。 開始するための&1; つのモジュールがあります。 
 
 Visual Studio のソリューション エクスプローラー ウィンドウには、すべてのファイル、検索パス、Python 環境などの、開いているプロジェクトが表示されます。 新しい項目を追加するには、プロジェクト フォルダーを選択し、コンテキスト メニュー (右のポインター ボタンを押す) から [追加]、[新しい項目] の順に選択します。 ダイアログ内のいずれかの項目を選択し、項目の名前をカスタマイズして、その項目をプロジェクトに追加することができます。 
 
 ソリューション エクスプローラーにドラッグ アンドドロップできます。 既にファイルをプロジェクトのディレクトリ構造にコピーした場合は、ソリューション エクスプローラーの上部にある [すべてのファイルを表示] を選択できます。 その後、追加する項目を選択して、コンテキスト メニューから [プロジェクトに含める] を選択できます。 
 
 これらの手順は、非常に短い [youtube ビデオ](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)で視聴できます。 
 
## <a name="see-also"></a>関連項目 
 [Wiki ドキュメント](https://github.com/Microsoft/PTVS/wiki/Projects) 
 [PTVS の概要と詳細に関するビデオ](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
