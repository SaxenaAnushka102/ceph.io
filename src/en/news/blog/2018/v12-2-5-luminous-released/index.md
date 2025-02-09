---
title: "v12.2.5 Luminous released"
date: "2018-04-24"
author: "TheAnalyst"
tags:
  - "release"
  - "luminous"
---

This is the fifth bugfix release of Luminous v12.2.x long term stable release series. This release contains a range of bug fixes across all compoenents of Ceph. We recommend all the users of 12.2.x series to update.

## Notable Changes

- MGR
    
    The ceph-rest-api command-line tool included in the ceph-mon package has been obsoleted by the MGR “restful” module. The ceph-rest-api tool is hereby declared deprecated and will be dropped in Mimic.
    
    The MGR “restful” module provides similar functionality via a “pass through” method. See [http://docs.ceph.com/docs/luminous/mgr/restful](http://docs.ceph.com/docs/luminous/mgr/restful) for details.
- CephFS
    
    Upgrading an MDS cluster to 12.2.3+ will result in all active MDS exiting due to feature incompatibilities once an upgraded MDS comes online (even as standby). Operators may ignore the error messages and continue upgrading/restarting or follow this upgrade sequence:
    
    Reduce the number of ranks to 1 (ceph fs set <fs\_name> max\_mds 1), wait for all other MDS to deactivate, leaving the one active MDS, upgrade the single active MDS, then upgrade/start standbys. Finally, restore the previous max\_mds.
    
    See also: [https://tracker.ceph.com/issues/23172](https://tracker.ceph.com/issues/23172)

## Other Notable Changes

- add –add-bucket and –move options to crushtool ([issue#23472](http://tracker.ceph.com/issues/23472), [issue#23471](http://tracker.ceph.com/issues/23471), [pr#21079](https://github.com/ceph/ceph/pull/21079), Kefu Chai)
- BlueStore.cc: \_balance\_bluefs\_freespace: assert(0 == “allocate failed, wtf”) ([issue#23063](http://tracker.ceph.com/issues/23063), [pr#21394](https://github.com/ceph/ceph/pull/21394), Igor Fedotov, xie xingguo, Sage Weil, Zac Medico)
- bluestore: correctly check all block devices to decide if journal is\_… ([issue#23173](http://tracker.ceph.com/issues/23173), [issue#23141](http://tracker.ceph.com/issues/23141), [pr#20651](https://github.com/ceph/ceph/pull/20651), Greg Farnum)
- bluestore: statfs available can go negative ([issue#23074](http://tracker.ceph.com/issues/23074), [pr#20554](https://github.com/ceph/ceph/pull/20554), Igor Fedotov, Sage Weil)
- build Debian installation packages failure ([issue#22856](http://tracker.ceph.com/issues/22856), [issue#22828](http://tracker.ceph.com/issues/22828), [pr#20250](https://github.com/ceph/ceph/pull/20250), Tone Zhang)
- build/ops: deb: move python-jinja2 dependency to mgr ([issue#22457](http://tracker.ceph.com/issues/22457), [pr#20748](https://github.com/ceph/ceph/pull/20748), Nathan Cutler)
- build/ops: deb: move python-jinja2 dependency to mgr ([issue#22457](http://tracker.ceph.com/issues/22457), [pr#21233](https://github.com/ceph/ceph/pull/21233), Nathan Cutler)
- build/ops: run-make-check.sh: fix SUSE support ([issue#22875](http://tracker.ceph.com/issues/22875), [issue#23178](http://tracker.ceph.com/issues/23178), [pr#20737](https://github.com/ceph/ceph/pull/20737), Nathan Cutler)
- cephfs-journal-tool: Fix Dumper destroyed before shutdown ([issue#22862](http://tracker.ceph.com/issues/22862), [issue#22734](http://tracker.ceph.com/issues/22734), [pr#20251](https://github.com/ceph/ceph/pull/20251), dongdong tao)
- ceph.in: print all matched commands if arg missing ([issue#22344](http://tracker.ceph.com/issues/22344), [issue#23186](http://tracker.ceph.com/issues/23186), [pr#20664](https://github.com/ceph/ceph/pull/20664), Luo Kexue, Kefu Chai)
- ceph-objectstore-tool command to trim the pg log ([issue#23242](http://tracker.ceph.com/issues/23242), [pr#20803](https://github.com/ceph/ceph/pull/20803), Josh Durgin, David Zafman)
- ceph osd force-create-pg cause all ceph-mon to crash and unable to come up again ([issue#22942](http://tracker.ceph.com/issues/22942), [pr#20399](https://github.com/ceph/ceph/pull/20399), Sage Weil)
- ceph-volume: adds raw device support to ‘lvm list’ ([issue#23140](http://tracker.ceph.com/issues/23140), [pr#20647](https://github.com/ceph/ceph/pull/20647), Andrew Schoen)
- ceph-volume: allow parallel creates ([issue#23757](http://tracker.ceph.com/issues/23757), [pr#21509](https://github.com/ceph/ceph/pull/21509), Theofilos Mouratidis)
- ceph-volume: allow skipping systemd interactions on activate/create ([issue#23678](http://tracker.ceph.com/issues/23678), [pr#21538](https://github.com/ceph/ceph/pull/21538), Alfredo Deza)
- ceph-volume: automatic VDO detection ([issue#23581](http://tracker.ceph.com/issues/23581), [pr#21505](https://github.com/ceph/ceph/pull/21505), Alfredo Deza)
- ceph-volume be resilient to $PATH issues ([pr#20716](https://github.com/ceph/ceph/pull/20716), Alfredo Deza)
- ceph-volume: fix action plugins path in tox ([pr#20923](https://github.com/ceph/ceph/pull/20923), Guillaume Abrioux)
- ceph-volume Implement an ‘activate all’ to help with dense servers or migrating OSDs ([pr#21533](https://github.com/ceph/ceph/pull/21533), Alfredo Deza)
- ceph-volume improve robustness when reloading vms in tests ([pr#21072](https://github.com/ceph/ceph/pull/21072), Alfredo Deza)
- ceph-volume lvm.activate error if no bluestore OSDs are found ([issue#23644](http://tracker.ceph.com/issues/23644), [pr#21335](https://github.com/ceph/ceph/pull/21335), Alfredo Deza)
- ceph-volume: Nits noticed while studying code ([pr#21565](https://github.com/ceph/ceph/pull/21565), Dan Mick)
- ceph-volume tests alleviate libvirt timeouts when reloading ([issue#23163](http://tracker.ceph.com/issues/23163), [pr#20754](https://github.com/ceph/ceph/pull/20754), Alfredo Deza)
- ceph-volume update man page for prepare/activate flags ([pr#21574](https://github.com/ceph/ceph/pull/21574), Alfredo Deza)
- ceph-volume: Using –readonly for {vg|pv|lv}s commands ([pr#21519](https://github.com/ceph/ceph/pull/21519), Erwan Velu)
- client: allow client to use caps that are revoked but not yet returned ([issue#23028](http://tracker.ceph.com/issues/23028), [issue#23314](http://tracker.ceph.com/issues/23314), [pr#20904](https://github.com/ceph/ceph/pull/20904), Jeff Layton)
- : Client:Fix readdir bug ([issue#22936](http://tracker.ceph.com/issues/22936), [pr#20356](https://github.com/ceph/ceph/pull/20356), dongdong tao)
- client: release revoking Fc after invalidate cache ([issue#22652](http://tracker.ceph.com/issues/22652), [pr#20342](https://github.com/ceph/ceph/pull/20342), “Yan, Zheng”)
- Client: setattr should drop “Fs” rather than “As” for mtime and size ([issue#22935](http://tracker.ceph.com/issues/22935), [pr#20354](https://github.com/ceph/ceph/pull/20354), dongdong tao)
- client: use either dentry\_invalidate\_cb or remount\_cb to invalidate k… ([issue#23355](http://tracker.ceph.com/issues/23355), [pr#20960](https://github.com/ceph/ceph/pull/20960), Zhi Zhang)
- cls/rbd: group\_image\_list incorrectly flagged as RW ([issue#23407](http://tracker.ceph.com/issues/23407), [issue#23388](http://tracker.ceph.com/issues/23388), [pr#20967](https://github.com/ceph/ceph/pull/20967), Jason Dillaman)
- cls/rgw: fix bi\_log\_iterate\_entries return wrong truncated ([issue#22737](http://tracker.ceph.com/issues/22737), [issue#23225](http://tracker.ceph.com/issues/23225), [pr#21054](https://github.com/ceph/ceph/pull/21054), Tianshan Qu)
- cmake: rbd resource agent needs to be executable ([issue#22980](http://tracker.ceph.com/issues/22980), [pr#20617](https://github.com/ceph/ceph/pull/20617), Tim Bishop)
- common/dns\_resolv.cc: Query for AAAA-record if ms\_bind\_ipv6 is True ([issue#23078](http://tracker.ceph.com/issues/23078), [issue#23174](http://tracker.ceph.com/issues/23174), [pr#20710](https://github.com/ceph/ceph/pull/20710), Wido den Hollander)
- common/ipaddr: Do not select link-local IPv6 addresses ([issue#21813](http://tracker.ceph.com/issues/21813), [pr#21111](https://github.com/ceph/ceph/pull/21111), Willem Jan Withagen)
- common: omit short option for id in help for clients ([issue#23156](http://tracker.ceph.com/issues/23156), [issue#23041](http://tracker.ceph.com/issues/23041), [pr#20654](https://github.com/ceph/ceph/pull/20654), Patrick Donnelly)
- common: should not check for VERSION\_ID ([issue#23477](http://tracker.ceph.com/issues/23477), [issue#23478](http://tracker.ceph.com/issues/23478), [pr#21090](https://github.com/ceph/ceph/pull/21090), Kefu Chai, Shengjing Zhu)
- config: Change bluestore\_cache\_kv\_max to type INT64 ([pr#20334](https://github.com/ceph/ceph/pull/20334), Zhi Zhang)
- Couldn’t init storage provider (RADOS) ([issue#23349](http://tracker.ceph.com/issues/23349), [issue#22351](http://tracker.ceph.com/issues/22351), [pr#20896](https://github.com/ceph/ceph/pull/20896), Brad Hubbard)
- doc: Add missing pg states from doc ([issue#23113](http://tracker.ceph.com/issues/23113), [pr#20584](https://github.com/ceph/ceph/pull/20584), David Zafman)
- doc: outline upgrade procedure for mds cluster ([issue#23634](http://tracker.ceph.com/issues/23634), [issue#23568](http://tracker.ceph.com/issues/23568), [pr#21352](https://github.com/ceph/ceph/pull/21352), Patrick Donnelly)
- doc/rgw: add page for http frontend configuration ([issue#13523](http://tracker.ceph.com/issues/13523), [issue#22884](http://tracker.ceph.com/issues/22884), [pr#20242](https://github.com/ceph/ceph/pull/20242), Casey Bodley)
- doc: rgw: mention the civetweb support for binding to multiple ports ([issue#20942](http://tracker.ceph.com/issues/20942), [issue#23317](http://tracker.ceph.com/issues/23317), [pr#20906](https://github.com/ceph/ceph/pull/20906), Abhishek Lekshmanan)
- docs fix ceph-volume missing sub-commands ([pr#20691](https://github.com/ceph/ceph/pull/20691), Katie Holly, Yao Zongyou, David Galloway, Sage Weil, Alfredo Deza)
- doc: update man page to explain ceph-volume support bluestore ([issue#23142](http://tracker.ceph.com/issues/23142), [issue#22663](http://tracker.ceph.com/issues/22663), [pr#20679](https://github.com/ceph/ceph/pull/20679), lijing)
- Double free in rados\_getxattrs\_next ([issue#22940](http://tracker.ceph.com/issues/22940), [issue#22042](http://tracker.ceph.com/issues/22042), [pr#20358](https://github.com/ceph/ceph/pull/20358), Gu Zhongyan)
- fixes for openssl & libcurl ([issue#23239](http://tracker.ceph.com/issues/23239), [issue#23245](http://tracker.ceph.com/issues/23245), [issue#22951](http://tracker.ceph.com/issues/22951), [issue#23221](http://tracker.ceph.com/issues/23221), [issue#23203](http://tracker.ceph.com/issues/23203), [pr#20722](https://github.com/ceph/ceph/pull/20722), Marcus Watts, Abhishek Lekshmanan, Jesse Williamson)
- invalid JSON returned when querying pool parameters ([issue#23312](http://tracker.ceph.com/issues/23312), [issue#23200](http://tracker.ceph.com/issues/23200), [pr#20890](https://github.com/ceph/ceph/pull/20890), Chang Liu)
- is\_qemu\_running in qemu\_rebuild\_object\_map.sh and qemu\_dynamic\_features.sh may return false positive ([issue#23524](http://tracker.ceph.com/issues/23524), [pr#21192](https://github.com/ceph/ceph/pull/21192), Mykola Golub)
- \[journal\] allocating a new tag after acquiring the lock should use on-disk committed position ([issue#23011](http://tracker.ceph.com/issues/23011), [issue#22945](http://tracker.ceph.com/issues/22945), [pr#20454](https://github.com/ceph/ceph/pull/20454), Jason Dillaman)
- journal: Message too long error when appending journal ([issue#23545](http://tracker.ceph.com/issues/23545), [issue#23526](http://tracker.ceph.com/issues/23526), [pr#21216](https://github.com/ceph/ceph/pull/21216), Mykola Golub)
- legal: remove doc license ambiguity ([issue#23410](http://tracker.ceph.com/issues/23410), [issue#23336](http://tracker.ceph.com/issues/23336), [pr#20988](https://github.com/ceph/ceph/pull/20988), Nathan Cutler)
- librados: make OPERATION\_FULL\_FORCE the default for rados\_remove() ([issue#23114](http://tracker.ceph.com/issues/23114), [issue#22413](http://tracker.ceph.com/issues/22413), [pr#20585](https://github.com/ceph/ceph/pull/20585), Kefu Chai)
- librados/snap\_set\_diff: don’t assert on empty snapset ([issue#23423](http://tracker.ceph.com/issues/23423), [pr#20991](https://github.com/ceph/ceph/pull/20991), Mykola Golub)
- librbd: potential crash if object map check encounters error ([issue#22857](http://tracker.ceph.com/issues/22857), [issue#22819](http://tracker.ceph.com/issues/22819), [pr#20253](https://github.com/ceph/ceph/pull/20253), Jason Dillaman)
- log: Fix AddressSanitizer: new-delete-type-mismatch ([issue#23324](http://tracker.ceph.com/issues/23324), [issue#23412](http://tracker.ceph.com/issues/23412), [pr#20998](https://github.com/ceph/ceph/pull/20998), Brad Hubbard)
- mds: add uptime to MDS status ([issue#23150](http://tracker.ceph.com/issues/23150), [pr#20626](https://github.com/ceph/ceph/pull/20626), Patrick Donnelly)
- mds: FAILED assert (p != active\_requests.end()) in MDRequestRef MDCache::request\_get(metareqid\_t) ([issue#23154](http://tracker.ceph.com/issues/23154), [issue#23059](http://tracker.ceph.com/issues/23059), [pr#21176](https://github.com/ceph/ceph/pull/21176), “Yan, Zheng”)
- mds: fix session reference leak ([issue#22821](http://tracker.ceph.com/issues/22821), [issue#22969](http://tracker.ceph.com/issues/22969), [pr#20432](https://github.com/ceph/ceph/pull/20432), “Yan, Zheng”)
- mds: optimize getattr file size ([issue#23013](http://tracker.ceph.com/issues/23013), [issue#22925](http://tracker.ceph.com/issues/22925), [pr#20455](https://github.com/ceph/ceph/pull/20455), “Yan, Zheng”)
- mgr: Backport recent prometheus exporter changes ([pr#20642](https://github.com/ceph/ceph/pull/20642), Jan Fajerski, Boris Ranto)
- mgr: Backport recent prometheus rgw changes ([pr#21492](https://github.com/ceph/ceph/pull/21492), Jan Fajerski, John Spray, Boris Ranto, Rubab-Syed)
- mgr/balancer: pool-specific optimization support and bug fixes ([pr#20359](https://github.com/ceph/ceph/pull/20359), xie xingguo)
- mgr: die on bind() failure ([issue#23175](http://tracker.ceph.com/issues/23175), [pr#20712](https://github.com/ceph/ceph/pull/20712), John Spray)
- mgr: fix MSG\_MGR\_MAP handling ([issue#23409](http://tracker.ceph.com/issues/23409), [pr#20973](https://github.com/ceph/ceph/pull/20973), Gu Zhongyan)
- mgr: prometheus: fix PG state names ([pr#21365](https://github.com/ceph/ceph/pull/21365), John Spray)
- mgr: prometheus: set metadata metrics value to ‘1’ (#22717) ([pr#20254](https://github.com/ceph/ceph/pull/20254), Konstantin Shalygin)
- mgr: quieten logging on missing OSD stats ([issue#23224](http://tracker.ceph.com/issues/23224), [pr#21053](https://github.com/ceph/ceph/pull/21053), John Spray)
- mgr/zabbix: Backports to Luminous ([pr#20781](https://github.com/ceph/ceph/pull/20781), Wido den Hollander)
- mon: allow removal of tier of ec overwritable pool ([issue#22971](http://tracker.ceph.com/issues/22971), [issue#22754](http://tracker.ceph.com/issues/22754), [pr#20433](https://github.com/ceph/ceph/pull/20433), Patrick Donnelly)
- mon: ops get stuck in “resend forwarded message to leader” ([issue#22114](http://tracker.ceph.com/issues/22114), [issue#23077](http://tracker.ceph.com/issues/23077), [pr#21016](https://github.com/ceph/ceph/pull/21016), Kefu Chai, Greg Farnum)
- mon, osd: fix potential collided \*Up Set\* after PG remapping ([issue#23118](http://tracker.ceph.com/issues/23118), [pr#20829](https://github.com/ceph/ceph/pull/20829), xie xingguo)
- mon/OSDMonitor.cc: fix expected\_num\_objects interpret error ([issue#22530](http://tracker.ceph.com/issues/22530), [issue#23315](http://tracker.ceph.com/issues/23315), [pr#20907](https://github.com/ceph/ceph/pull/20907), Yang Honggang)
- mon: update PaxosService::cached\_first\_committed in PaxosService::may… ([issue#23626](http://tracker.ceph.com/issues/23626), [issue#11332](http://tracker.ceph.com/issues/11332), [pr#21328](https://github.com/ceph/ceph/pull/21328), Xuehan Xu, yupeng chen)
- msg/async: size of EventCenter::file\_events should be greater than fd ([issue#23253](http://tracker.ceph.com/issues/23253), [issue#23306](http://tracker.ceph.com/issues/23306), [pr#20867](https://github.com/ceph/ceph/pull/20867), Yupeng Chen)
- Objecter: add ignore overlay flag if got redirect reply ([pr#20766](https://github.com/ceph/ceph/pull/20766), Ting Yi Lin)
- os/bluestore: avoid overhead of std::function in blob\_t ([pr#20674](https://github.com/ceph/ceph/pull/20674), Radoslaw Zarzynski)
- os/bluestore: avoid unneeded BlobRefing in \_do\_read() ([pr#20675](https://github.com/ceph/ceph/pull/20675), Radoslaw Zarzynski)
- os/bluestore: backport fixes around \_reap\_collection ([pr#20964](https://github.com/ceph/ceph/pull/20964), Jianpeng Ma)
- os/bluestore: change the type of aio\_t:res to long ([issue#23527](http://tracker.ceph.com/issues/23527), [issue#23544](http://tracker.ceph.com/issues/23544), [pr#21231](https://github.com/ceph/ceph/pull/21231), kungf)
- os/bluestore: \_dump\_onode() don’t prolongate Onode anymore ([pr#20676](https://github.com/ceph/ceph/pull/20676), Radoslaw Zarzynski)
- os/bluestore: recalc\_allocated() when decoding bluefs\_fnode\_t ([issue#23256](http://tracker.ceph.com/issues/23256), [issue#23212](http://tracker.ceph.com/issues/23212), [pr#20771](https://github.com/ceph/ceph/pull/20771), Jianpeng Ma, Igor Fedotov, Kefu Chai)
- os/bluestore: trim cache every 50ms (instead of 200ms) ([issue#23226](http://tracker.ceph.com/issues/23226), [pr#21059](https://github.com/ceph/ceph/pull/21059), Sage Weil)
- osd: add numpg\_removing metric ([pr#20785](https://github.com/ceph/ceph/pull/20785), Sage Weil)
- osdc/Journaler: make sure flush() writes enough data ([issue#22967](http://tracker.ceph.com/issues/22967), [issue#22824](http://tracker.ceph.com/issues/22824), [pr#20431](https://github.com/ceph/ceph/pull/20431), “Yan, Zheng”)
- osd: do not release\_reserved\_pushes when requeuing ([pr#21229](https://github.com/ceph/ceph/pull/21229), Sage Weil)
- osd: Fix assert when checking missing version ([issue#21218](http://tracker.ceph.com/issues/21218), [issue#23024](http://tracker.ceph.com/issues/23024), [pr#20495](https://github.com/ceph/ceph/pull/20495), David Zafman)
- osd: objecter sends out of sync with pg epochs for proxied ops ([issue#22123](http://tracker.ceph.com/issues/22123), [issue#23075](http://tracker.ceph.com/issues/23075), [pr#20609](https://github.com/ceph/ceph/pull/20609), Sage Weil)
- osd/OSDMap: skip out/crush-out osds ([pr#20840](https://github.com/ceph/ceph/pull/20840), xie xingguo)
- osd/osd\_types: fix pg\_pool\_t encoding for hammer ([pr#21283](https://github.com/ceph/ceph/pull/21283), Sage Weil)
- osd: remove cost from mclock op queues; cost not handled well in dmcl… ([pr#21426](https://github.com/ceph/ceph/pull/21426), J. Eric Ivancich)
- osd: Remove partially created pg known as DNE ([issue#23160](http://tracker.ceph.com/issues/23160), [issue#21833](http://tracker.ceph.com/issues/21833), [pr#20668](https://github.com/ceph/ceph/pull/20668), David Zafman)
- osd: resend osd\_pgtemp if it’s not acked ([issue#23610](http://tracker.ceph.com/issues/23610), [issue#23630](http://tracker.ceph.com/issues/23630), [pr#21330](https://github.com/ceph/ceph/pull/21330), Kefu Chai)
- osd: treat successful and erroroneous writes the same for log trimming ([issue#23323](http://tracker.ceph.com/issues/23323), [issue#22050](http://tracker.ceph.com/issues/22050), [pr#20851](https://github.com/ceph/ceph/pull/20851), Josh Durgin)
- os/filestore: fix do\_copy\_range replay bug ([issue#23351](http://tracker.ceph.com/issues/23351), [issue#23298](http://tracker.ceph.com/issues/23298), [pr#20957](https://github.com/ceph/ceph/pull/20957), Sage Weil)
- parent blocks are still seen after a whole-object discard ([issue#23304](http://tracker.ceph.com/issues/23304), [issue#23285](http://tracker.ceph.com/issues/23285), [pr#20860](https://github.com/ceph/ceph/pull/20860), Ilya Dryomov, Jason Dillaman)
- PendingReleaseNotes: add note about upgrading MDS ([issue#23414](http://tracker.ceph.com/issues/23414), [pr#21001](https://github.com/ceph/ceph/pull/21001), Patrick Donnelly)
- : qa: adjust cephfs full test for kclient ([issue#22966](http://tracker.ceph.com/issues/22966), [issue#22886](http://tracker.ceph.com/issues/22886), [pr#20417](https://github.com/ceph/ceph/pull/20417), “Yan, Zheng”)
- qa: ignore io pause warnings in mds-full test ([issue#23062](http://tracker.ceph.com/issues/23062), [issue#22990](http://tracker.ceph.com/issues/22990), [pr#20525](https://github.com/ceph/ceph/pull/20525), Patrick Donnelly)
- qa: ignore MON\_DOWN while thrashing mons ([issue#23061](http://tracker.ceph.com/issues/23061), [pr#20523](https://github.com/ceph/ceph/pull/20523), Patrick Donnelly)
- qa/rgw: remove some civetweb overrides for beast testing ([issue#23002](http://tracker.ceph.com/issues/23002), [issue#23176](http://tracker.ceph.com/issues/23176), [pr#20736](https://github.com/ceph/ceph/pull/20736), Casey Bodley)
- qa: src/test/libcephfs/test.cc:376: Expected: (len) > (0), actual: -34 vs 0 ([issue#22383](http://tracker.ceph.com/issues/22383), [issue#22221](http://tracker.ceph.com/issues/22221), [pr#21173](https://github.com/ceph/ceph/pull/21173), Patrick Donnelly)
- qa: synchronize kcephfs suites with fs/multimds ([issue#22891](http://tracker.ceph.com/issues/22891), [issue#22627](http://tracker.ceph.com/issues/22627), [pr#20302](https://github.com/ceph/ceph/pull/20302), Patrick Donnelly)
- qa/tests - added tag: v12.2.2 to be used by client.1 ([pr#21452](https://github.com/ceph/ceph/pull/21452), Yuri Weinstein)
- qa/tests - Change machine type from ‘vps’ to ‘ovh’ as ‘vps’ does not … ([pr#21031](https://github.com/ceph/ceph/pull/21031), Yuri Weinstein)
- qa/workunits/rados/test-upgrade-to-mimic.sh: fix tee output ([pr#21506](https://github.com/ceph/ceph/pull/21506), Sage Weil)
- qa/workunits/rbd: switch devstack tempest to 17.2.0 tag ([issue#23177](http://tracker.ceph.com/issues/23177), [issue#22961](http://tracker.ceph.com/issues/22961), [pr#20715](https://github.com/ceph/ceph/pull/20715), Jason Dillaman)
- radosgw-admin data sync run crashes ([issue#23180](http://tracker.ceph.com/issues/23180), [pr#20762](https://github.com/ceph/ceph/pull/20762), lvshanchun)
- rbd-mirror: fix potential infinite loop when formatting status message ([issue#22964](http://tracker.ceph.com/issues/22964), [issue#22932](http://tracker.ceph.com/issues/22932), [pr#20416](https://github.com/ceph/ceph/pull/20416), Mykola Golub)
- rbd-nbd: fix ebusy when do map ([issue#23542](http://tracker.ceph.com/issues/23542), [issue#23528](http://tracker.ceph.com/issues/23528), [pr#21230](https://github.com/ceph/ceph/pull/21230), Li Wang)
- rgw: add radosgw-admin sync error trim to trim sync error log ([issue#23302](http://tracker.ceph.com/issues/23302), [pr#20859](https://github.com/ceph/ceph/pull/20859), fang yuxiang)
- rgw: add xml output header in RGWCopyObj\_ObjStore\_S3 response msg ([issue#22416](http://tracker.ceph.com/issues/22416), [issue#22635](http://tracker.ceph.com/issues/22635), [pr#19883](https://github.com/ceph/ceph/pull/19883), Enming Zhang)
- rgw: Admin API Support for bucket quota change ([issue#23357](http://tracker.ceph.com/issues/23357), [issue#21811](http://tracker.ceph.com/issues/21811), [pr#20885](https://github.com/ceph/ceph/pull/20885), Jeegn Chen)
- rgw: allow beast frontend to listen on specific IP address ([issue#22858](http://tracker.ceph.com/issues/22858), [issue#22778](http://tracker.ceph.com/issues/22778), [pr#20252](https://github.com/ceph/ceph/pull/20252), Yuan Zhou)
- rgw: can’t download object with range when compression enabled ([issue#23146](http://tracker.ceph.com/issues/23146), [issue#23179](http://tracker.ceph.com/issues/23179), [issue#22852](http://tracker.ceph.com/issues/22852), [pr#20741](https://github.com/ceph/ceph/pull/20741), fang yuxiang)
- rgw: data sync of versioned objects, note updating bi marker ([issue#23025](http://tracker.ceph.com/issues/23025), [pr#21214](https://github.com/ceph/ceph/pull/21214), Yehuda Sadeh)
- RGW doesn’t check time skew in auth v4 http header request ([issue#23252](http://tracker.ceph.com/issues/23252), [issue#22766](http://tracker.ceph.com/issues/22766), [issue#22439](http://tracker.ceph.com/issues/22439), [issue#22418](http://tracker.ceph.com/issues/22418), [pr#20072](https://github.com/ceph/ceph/pull/20072), Bingyin Zhang, Casey Bodley)
- rgw\_file: avoid evaluating nullptr for readdir offset ([issue#22889](http://tracker.ceph.com/issues/22889), [pr#20345](https://github.com/ceph/ceph/pull/20345), Matt Benjamin)
- rgw: fix crash with rgw\_run\_sync\_thread false ([issue#23318](http://tracker.ceph.com/issues/23318), [issue#20448](http://tracker.ceph.com/issues/20448), [pr#20932](https://github.com/ceph/ceph/pull/20932), Orit Wasserman)
- rgw: fix memory fragmentation problem reading data from client ([issue#23347](http://tracker.ceph.com/issues/23347), [pr#20953](https://github.com/ceph/ceph/pull/20953), Marcus Watts)
- rgw: fix mutlisite read-write issues ([issue#23690](http://tracker.ceph.com/issues/23690), [issue#22804](http://tracker.ceph.com/issues/22804), [pr#21390](https://github.com/ceph/ceph/pull/21390), Niu Pengju)
- rgw: fix the max-uploads parameter not work ([issue#23020](http://tracker.ceph.com/issues/23020), [issue#22825](http://tracker.ceph.com/issues/22825), [pr#20476](https://github.com/ceph/ceph/pull/20476), Xin Liao)
- rgw\_log, rgw\_file: account for new required envvars ([issue#23192](http://tracker.ceph.com/issues/23192), [issue#21942](http://tracker.ceph.com/issues/21942), [pr#20672](https://github.com/ceph/ceph/pull/20672), Matt Benjamin)
- rgw: log the right http status code in civetweb frontend’s access log ([issue#22812](http://tracker.ceph.com/issues/22812), [issue#22538](http://tracker.ceph.com/issues/22538), [pr#20157](https://github.com/ceph/ceph/pull/20157), Yao Zongyou)
- rgw: parse old rgw\_obj with namespace correctly ([issue#23102](http://tracker.ceph.com/issues/23102), [issue#22982](http://tracker.ceph.com/issues/22982), [pr#20586](https://github.com/ceph/ceph/pull/20586), Yehuda Sadeh)
- rgw recalculate stats option added ([issue#23691](http://tracker.ceph.com/issues/23691), [issue#23720](http://tracker.ceph.com/issues/23720), [issue#23335](http://tracker.ceph.com/issues/23335), [issue#23322](http://tracker.ceph.com/issues/23322), [pr#21393](https://github.com/ceph/ceph/pull/21393), Abhishek Lekshmanan)
- rgw: reject encrypted object COPY before supported ([issue#23232](http://tracker.ceph.com/issues/23232), [issue#23346](http://tracker.ceph.com/issues/23346), [pr#20937](https://github.com/ceph/ceph/pull/20937), Jeegn Chen)
- rgw: rgw: reshard cancel command should clear bucket resharding flag ([issue#21619](http://tracker.ceph.com/issues/21619), [pr#21389](https://github.com/ceph/ceph/pull/21389), Orit Wasserman)
- rgw: s3website error handler uses original object name ([issue#23201](http://tracker.ceph.com/issues/23201), [issue#23310](http://tracker.ceph.com/issues/23310), [pr#20889](https://github.com/ceph/ceph/pull/20889), Casey Bodley)
- rgw: upldate the max-buckets when the quota is uploaded ([issue#23022](http://tracker.ceph.com/issues/23022), [pr#20477](https://github.com/ceph/ceph/pull/20477), zhaokun)
- rgw: usage log fixes ([issue#23686](http://tracker.ceph.com/issues/23686), [issue#23758](http://tracker.ceph.com/issues/23758), [pr#21388](https://github.com/ceph/ceph/pull/21388), Yehuda Sadeh, Greg Farnum, Robin H. Johnson)
- rocksdb: incorporate the fix in RocksDB for no fast CRC32 path ([issue#22534](http://tracker.ceph.com/issues/22534), [pr#20825](https://github.com/ceph/ceph/pull/20825), Radoslaw Zarzynski)
- scrub errors not cleared on replicas can cause inconsistent pg state when replica takes over primary ([issue#23267](http://tracker.ceph.com/issues/23267), [pr#21103](https://github.com/ceph/ceph/pull/21103), David Zafman)
- snapmapper inconsistency, crash on luminous ([issue#23500](http://tracker.ceph.com/issues/23500), [pr#21118](https://github.com/ceph/ceph/pull/21118), Sage Weil)
- Special scrub handling of hinfo\_key errors ([issue#23654](http://tracker.ceph.com/issues/23654), [issue#23428](http://tracker.ceph.com/issues/23428), [issue#23364](http://tracker.ceph.com/issues/23364), [pr#21397](https://github.com/ceph/ceph/pull/21397), David Zafman)
- src: s/–use-wheel// ([pr#21177](https://github.com/ceph/ceph/pull/21177), Kefu Chai)
- systemd: Wait 10 seconds before restarting ceph-mgr ([issue#23083](http://tracker.ceph.com/issues/23083), [issue#23101](http://tracker.ceph.com/issues/23101), [pr#20604](https://github.com/ceph/ceph/pull/20604), Wido den Hollander)
- test\_admin\_socket.sh may fail on wait\_for\_clean ([issue#23507](http://tracker.ceph.com/issues/23507), [pr#21124](https://github.com/ceph/ceph/pull/21124), Mykola Golub)
- test/ceph-disk: specify the python used for creating venv ([issue#23281](http://tracker.ceph.com/issues/23281), [pr#20817](https://github.com/ceph/ceph/pull/20817), Kefu Chai)
- TestLibRBD.RenameViaLockOwner may still fail with -ENOENT ([issue#23152](http://tracker.ceph.com/issues/23152), [issue#23068](http://tracker.ceph.com/issues/23068), [pr#20628](https://github.com/ceph/ceph/pull/20628), Mykola Golub)
- test/librbd: utilize unique pool for cache tier testing ([issue#23064](http://tracker.ceph.com/issues/23064), [issue#11502](http://tracker.ceph.com/issues/11502), [pr#20550](https://github.com/ceph/ceph/pull/20550), Jason Dillaman)
- test/pybind/test\_rbd: allow v1 images for testing ([pr#21471](https://github.com/ceph/ceph/pull/21471), Sage Weil)
- test: Replace bc command with printf command ([pr#21015](https://github.com/ceph/ceph/pull/21015), David Zafman)
- tests: drop upgrade/jewel-x/point-to-point-x in luminous and master ([issue#23159](http://tracker.ceph.com/issues/23159), [issue#22888](http://tracker.ceph.com/issues/22888), [pr#20641](https://github.com/ceph/ceph/pull/20641), Nathan Cutler)
- tests: ENGINE Error in ‘start’ listener <bound in rados ([issue#23606](http://tracker.ceph.com/issues/23606), [pr#21307](https://github.com/ceph/ceph/pull/21307), John Spray)
- tests: rgw: swift tests target ceph-luminous branch ([pr#21048](https://github.com/ceph/ceph/pull/21048), Nathan Cutler)
- tests: unittest\_pglog timeout ([issue#23522](http://tracker.ceph.com/issues/23522), [issue#23504](http://tracker.ceph.com/issues/23504), [pr#21134](https://github.com/ceph/ceph/pull/21134), Nathan Cutler)
- Update mgr/restful documentation ([issue#23230](http://tracker.ceph.com/issues/23230), [pr#20725](https://github.com/ceph/ceph/pull/20725), Boris Ranto)
