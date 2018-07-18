---
title: 64 ビット デバッガー COM クラスの登録の移行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/10/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
author: gregg-miskelly
ms.author: greggm
manager: douge
ms.workload:
- greggm
ms.openlocfilehash: 28516038170dd34028d11bf9a070cf265ecfd830
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140447"
---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>64 ビット デバッガー COM クラスの登録を移行します。

(Regasm、regsvr32 を使用して、レジストリへの直接書き込み、)、HKEY_CLASSES_ROOT に COM クラスを登録し、msvsmon.exe (リモート デバッガー) に読み込まれるデバッガー拡張機能には、これが可能になりことがなく msvsmon にこの登録を提供HKEY_CLASSES_ROOT に書き込む。 これは、従来の .NET デバッガーの式エバリュエーター、または、msvsmon.exe プロセスの読み込みに構成されているデバッグ エンジンに影響します。

## <a name="msvsmon-comclass-def"></a>msvsmon-def comclass

この手法を使用するには、msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64) の横にある *.msvsmon comclass-def.json ファイルを追加します。

いずれかの管理、登録する msvsmon-def comclass ファイルの例と 1 つのネイティブ クラスを次に示します。

ファイル名: MyCompany.MyExample.msvsmon comclass def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```
