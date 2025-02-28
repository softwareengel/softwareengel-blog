﻿---
layout: post
title: mysql mariadb docker sql   
categories: [db]
tags: [db, mysql, mariadb]
--- 
# MySql / MariaDB 

## Install MariaDB in Docker 
    
    mkdir -p ~/data/mariadb
    sudo docker run --name my-mariadb -e MYSQL_ROOT_PASSWORD=p -d mariadb -p 3306:3306 -v ~/data/mariadb:/var/lib/mariadb/data 

## Zeit SQL
```sql
    select current_date, CURRENT_TIME, CURRENT_TIMESTAMP, 
    LOCALTIME, MAKETIME (3,3,3), SEC_TO_TIME(600),
    TIMEDIFF(600600, MAKETIME (3,3,3)),  UTC_TIME , UTC_TIME < LOCALTIME 
```

## Prozedur SQL
```sql 
    USE `fom_skripts`;
    DROP procedure IF EXISTS `new_procedure`;

    DELIMITER $$
    USE `fom_skripts`$$
    CREATE PROCEDURE `fom_skripts`.`new_procedure` ()
    BEGIN
    -- info 
    END$$

    DELIMITER ;
```

## Function SQL 
```sql 
    USE `fom_skripts`;
    DROP function IF EXISTS `new_function`;

    DELIMITER $$
    USE `fom_skripts`$$
    CREATE FUNCTION `fom_skripts`.`new_function` ()
    RETURNS INTEGER
    BEGIN

    RETURN 1;
    END$$

    DELIMITER ;
```
---
 ```sql 
    CREATE DEFINER=`root`@`localhost` PROCEDURE `create Proc 1`()
    LANGUAGE SQL
    NOT DETERMINISTIC
    CONTAINS SQL
    SQL SECURITY DEFINER
    COMMENT ''
    BEGIN
    START TRANSACTION ;
    drop table `fom_skripts`.`t_tmp`;

    CREATE  TABLE `fom_skripts`.`T_TMP` (
      `idT_TMP` INT NOT NULL ,
      `T_TMPcol1VC200` VARCHAR(200) NULL ,
      `T_TMPcol2DATETIME` DATETIME NULL ,
      `T_TMPcol3DBL` DOUBLE NULL ,
      PRIMARY KEY (`idT_TMP`) );
    COMMIT;

    END
```     
--- 
```sql 
    CREATE DEFINER=`root`@`localhost` PROCEDURE `proc_call`()
    LANGUAGE SQL
    NOT DETERMINISTIC
    CONTAINS SQL
    SQL SECURITY DEFINER
    COMMENT ''
    BEGIN

    -- DROP FUNCTION IF EXISTS `function1`; -- drop function geht nicht in function

    CALL `create Proc 1`();

    END
```
--- 
```sql 
    ALTER DATABASE `fom_skripts` COLLATE 'utf8_unicode_ci';
```

```sql 
    SHOW GLOBAL VARIABLES;
```


    "aria_block_size"	"8192"
    "aria_checkpoint_interval"	"30"
    "aria_checkpoint_log_activity"	"1048576"
    "aria_force_start_after_recovery_failures"	"0"
    "aria_group_commit"	"none"
    "aria_group_commit_interval"	"0"
    "aria_log_file_size"	"1073741824"
    "aria_log_purge_type"	"immediate"
    "aria_max_sort_file_size"	"9223372036853727232"
    "aria_page_checksum"	"ON"
    "aria_pagecache_age_threshold"	"300"
    "aria_pagecache_buffer_size"	"134217728"
    "aria_pagecache_division_limit"	"100"
    "aria_recover"	"NORMAL"
    "aria_repair_threads"	"1"
    "aria_sort_buffer_size"	"134217728"
    "aria_stats_method"	"nulls_unequal"
    "aria_sync_log_dir"	"NEWFILE"
    "aria_used_for_temp_tables"	"ON"
    "auto_increment_increment"	"1"
    "auto_increment_offset"	"1"
    "autocommit"	"ON"
    "automatic_sp_privileges"	"ON"
    "back_log"	"50"
    "basedir"	"C:\winbin\mariadb-5.5.29-winx64\"
    "big_tables"	"OFF"
    "binlog_annotate_row_events"	"OFF"
    "binlog_cache_size"	"32768"
    "binlog_checksum"	"NONE"
    "binlog_direct_non_transactional_updates"	"OFF"
    "binlog_format"	"STATEMENT"
    "binlog_optimize_thread_scheduling"	"ON"
    "binlog_stmt_cache_size"	"32768"
    "bulk_insert_buffer_size"	"8388608"
    "character_set_client"	"latin1"
    "character_set_connection"	"latin1"
    "character_set_database"	"latin1"
    "character_set_filesystem"	"binary"
    "character_set_results"	"latin1"
    "character_set_server"	"latin1"
    "character_set_system"	"utf8"
    "character_sets_dir"	"C:\winbin\mariadb-5.5.29-winx64\share\charsets\"
    "collation_connection"	"latin1_swedish_ci"
    "collation_database"	"latin1_swedish_ci"
    "collation_server"	"latin1_swedish_ci"
    "completion_type"	"NO_CHAIN"
    "concurrent_insert"	"AUTO"
    "connect_timeout"	"10"
    "datadir"	"C:\winbin\mariadb-5.5.29-winx64\data\"
    "date_format"	"%Y-%m-%d"
    "datetime_format"	"%Y-%m-%d %H:%i:%s"
    "deadlock_search_depth_long"	"15"
    "deadlock_search_depth_short"	"4"
    "deadlock_timeout_long"	"50000000"
    "deadlock_timeout_short"	"10000"
    "debug_no_thread_alarm"	"OFF"
    "default_storage_engine"	"InnoDB"
    "default_week_format"	"0"
    "delay_key_write"	"ON"
    "delayed_insert_limit"	"100"
    "delayed_insert_timeout"	"300"
    "delayed_queue_size"	"1000"
    "div_precision_increment"	"4"
    "engine_condition_pushdown"	"OFF"
    "event_scheduler"	"OFF"
    "expensive_subquery_limit"	"100"
    "expire_logs_days"	"0"
    "extra_max_connections"	"1"
    "extra_port"	"0"
    "flush"	"OFF"
    "flush_time"	"0"
    "foreign_key_checks"	"ON"
    "ft_boolean_syntax"	"+ -><()~*:""""&|"
    "ft_max_word_len"	"84"
    "ft_min_word_len"	"4"
    "ft_query_expansion_limit"	"20"
    "ft_stopword_file"	"(built-in)"
    "general_log"	"OFF"
    "general_log_file"	"T470p.log"
    "group_concat_max_len"	"1024"
    "have_compress"	"YES"
    "have_crypt"	"NO"
    "have_csv"	"YES"
    "have_dynamic_loading"	"YES"
    "have_geometry"	"YES"
    "have_innodb"	"YES"
    "have_ndbcluster"	"NO"
    "have_openssl"	"DISABLED"
    "have_partitioning"	"YES"
    "have_profiling"	"YES"
    "have_query_cache"	"YES"
    "have_rtree_keys"	"YES"
    "have_ssl"	"DISABLED"
    "have_symlink"	"DISABLED"
    "hostname"	"T470p"
    "ignore_builtin_innodb"	"OFF"
    "ignore_db_dirs"	""
    "init_connect"	""
    "init_file"	""
    "init_slave"	""
    "innodb_adaptive_flushing"	"ON"
    "innodb_adaptive_flushing_method"	"estimate"
    "innodb_adaptive_hash_index"	"ON"
    "innodb_adaptive_hash_index_partitions"	"1"
    "innodb_additional_mem_pool_size"	"8388608"
    "innodb_autoextend_increment"	"8"
    "innodb_autoinc_lock_mode"	"1"
    "innodb_blocking_buffer_pool_restore"	"OFF"
    "innodb_buffer_pool_instances"	"1"
    "innodb_buffer_pool_populate"	"OFF"
    "innodb_buffer_pool_restore_at_startup"	"0"
    "innodb_buffer_pool_shm_checksum"	"ON"
    "innodb_buffer_pool_shm_key"	"0"
    "innodb_buffer_pool_size"	"134217728"
    "innodb_change_buffering"	"all"
    "innodb_changed_pages_limit"	"1000000"
    "innodb_checkpoint_age_target"	"0"
    "innodb_checksums"	"ON"
    "innodb_commit_concurrency"	"0"
    "innodb_concurrency_tickets"	"500"
    "innodb_corrupt_table_action"	"assert"
    "innodb_data_file_path"	"ibdata1:10M:autoextend"
    "innodb_data_home_dir"	""
    "innodb_dict_size_limit"	"0"
    "innodb_doublewrite"	"ON"
    "innodb_doublewrite_file"	""
    "innodb_fake_changes"	"OFF"
    "innodb_fast_checksum"	"OFF"
    "innodb_fast_shutdown"	"1"
    "innodb_file_format"	"Antelope"
    "innodb_file_format_check"	"ON"
    "innodb_file_format_max"	"Antelope"
    "innodb_file_per_table"	"OFF"
    "innodb_flush_log_at_trx_commit"	"1"
    "innodb_flush_method"	""
    "innodb_flush_neighbor_pages"	"area"
    "innodb_force_load_corrupted"	"OFF"
    "innodb_force_recovery"	"0"
    "innodb_ibuf_accel_rate"	"100"
    "innodb_ibuf_active_contract"	"1"
    "innodb_ibuf_max_size"	"67092480"
    "innodb_import_table_from_xtrabackup"	"0"
    "innodb_io_capacity"	"200"
    "innodb_kill_idle_transaction"	"0"
    "innodb_large_prefix"	"OFF"
    "innodb_lazy_drop_table"	"0"
    "innodb_lock_wait_timeout"	"50"
    "innodb_locking_fake_changes"	"ON"
    "innodb_locks_unsafe_for_binlog"	"OFF"
    "innodb_log_block_size"	"512"
    "innodb_log_buffer_size"	"8388608"
    "innodb_log_file_size"	"5242880"
    "innodb_log_files_in_group"	"2"
    "innodb_log_group_home_dir"	".\"
    "innodb_max_bitmap_file_size"	"104857600"
    "innodb_max_dirty_pages_pct"	"75"
    "innodb_max_purge_lag"	"0"
    "innodb_merge_sort_block_size"	"1048576"
    "innodb_mirrored_log_groups"	"1"
    "innodb_old_blocks_pct"	"37"
    "innodb_old_blocks_time"	"0"
    "innodb_open_files"	"300"
    "innodb_page_size"	"16384"
    "innodb_purge_batch_size"	"20"
    "innodb_purge_threads"	"1"
    "innodb_random_read_ahead"	"OFF"
    "innodb_read_ahead"	"linear"
    "innodb_read_ahead_threshold"	"56"
    "innodb_read_io_threads"	"4"
    "innodb_recovery_stats"	"OFF"
    "innodb_recovery_update_relay_log"	"OFF"
    "innodb_replication_delay"	"0"
    "innodb_rollback_on_timeout"	"OFF"
    "innodb_rollback_segments"	"128"
    "innodb_show_locks_held"	"10"
    "innodb_show_verbose_locks"	"0"
    "innodb_spin_wait_delay"	"6"
    "innodb_stats_auto_update"	"1"
    "innodb_stats_method"	"nulls_equal"
    "innodb_stats_on_metadata"	"ON"
    "innodb_stats_sample_pages"	"8"
    "innodb_stats_update_need_lock"	"1"
    "innodb_strict_mode"	"OFF"
    "innodb_support_xa"	"ON"
    "innodb_sync_spin_loops"	"30"
    "innodb_table_locks"	"ON"
    "innodb_thread_concurrency"	"0"
    "innodb_thread_concurrency_timer_based"	"OFF"
    "innodb_thread_sleep_delay"	"10000"
    "innodb_track_changed_pages"	"OFF"
    "innodb_use_global_flush_log_at_trx_commit"	"ON"
    "innodb_use_native_aio"	"ON"
    "innodb_use_sys_malloc"	"ON"
    "innodb_use_sys_stats_table"	"OFF"
    "innodb_version"	"1.1.8-29.3"
    "innodb_write_io_threads"	"4"
    "interactive_timeout"	"28800"
    "join_buffer_size"	"131072"
    "join_buffer_space_limit"	"2097152"
    "join_cache_level"	"2"
    "keep_files_on_create"	"OFF"
    "key_buffer_size"	"134217728"
    "key_cache_age_threshold"	"300"
    "key_cache_block_size"	"1024"
    "key_cache_division_limit"	"100"
    "key_cache_segments"	"0"
    "large_files_support"	"ON"
    "large_page_size"	"0"
    "large_pages"	"OFF"
    "lc_messages"	"en_US"
    "lc_messages_dir"	""
    "lc_time_names"	"en_US"
    "license"	"GPL"
    "local_infile"	"ON"
    "lock_wait_timeout"	"31536000"
    "log"	"OFF"
    "log_bin"	"OFF"
    "log_bin_trust_function_creators"	"OFF"
    "log_error"	"C:\winbin\mariadb-5.5.29-winx64\data\T470p.err"
    "log_output"	"FILE"
    "log_queries_not_using_indexes"	"OFF"
    "log_slave_updates"	"OFF"
    "log_slow_filter"	"admin,filesort,filesort_on_disk,full_join,full_scan,query_cache,query_cache_miss,tmp_table,tmp_table_on_disk"
    "log_slow_queries"	"OFF"
    "log_slow_rate_limit"	"1"
    "log_slow_verbosity"	""
    "log_warnings"	"1"
    "long_query_time"	"10.000000"
    "low_priority_updates"	"OFF"
    "lower_case_file_system"	"ON"
    "lower_case_table_names"	"1"
    "master_verify_checksum"	"OFF"
    "max_allowed_packet"	"1048576"
    "max_binlog_cache_size"	"4294963200"
    "max_binlog_size"	"1073741824"
    "max_binlog_stmt_cache_size"	"4294963200"
    "max_connect_errors"	"10"
    "max_connections"	"151"
    "max_delayed_threads"	"20"
    "max_error_count"	"64"
    "max_heap_table_size"	"16777216"
    "max_insert_delayed_threads"	"20"
    "max_join_size"	"18446744073709551615"
    "max_length_for_sort_data"	"1024"
    "max_long_data_size"	"1048576"
    "max_prepared_stmt_count"	"16382"
    "max_relay_log_size"	"0"
    "max_seeks_for_key"	"4294967295"
    "max_sort_length"	"1024"
    "max_sp_recursion_depth"	"0"
    "max_tmp_tables"	"32"
    "max_user_connections"	"0"
    "max_write_lock_count"	"4294967295"
    "metadata_locks_cache_size"	"1024"
    "min_examined_row_limit"	"0"
    "mrr_buffer_size"	"262144"
    "multi_range_count"	"256"
    "myisam_block_size"	"1024"
    "myisam_data_pointer_size"	"6"
    "myisam_max_sort_file_size"	"2146435072"
    "myisam_mmap_size"	"18446744073709551615"
    "myisam_recover_options"	"DEFAULT"
    "myisam_repair_threads"	"1"
    "myisam_sort_buffer_size"	"8388608"
    "myisam_stats_method"	"nulls_unequal"
    "myisam_use_mmap"	"OFF"
    "named_pipe"	"OFF"
    "net_buffer_length"	"16384"
    "net_read_timeout"	"30"
    "net_retry_count"	"10"
    "net_write_timeout"	"60"
    "old"	"OFF"
    "old_alter_table"	"OFF"
    "old_passwords"	"OFF"
    "open_files_limit"	"3010"
    "optimizer_prune_level"	"1"
    "optimizer_search_depth"	"62"
    "optimizer_switch"	"index_merge=on,index_merge_union=on,index_merge_sort_union=on,index_merge_intersection=on,index_merge_sort_intersection=off,engine_condition_pushdown=off,index_condition_pushdown=on,derived_merge=on,derived_with_keys=on,firstmatch=on,loosescan=on,materialization=on,in_to_exists=on,semijoin=on,partial_match_rowid_merge=on,partial_match_table_scan=on,subquery_cache=on,mrr=off,mrr_cost_based=off,mrr_sort_keys=off,outer_join_with_cache=on,semijoin_with_cache=on,join_cache_incremental=on,join_cache_hashed=on,join_cache_bka=on,optimize_join_buffer_size=off,table_elimination=on,extended_keys=off"
    "performance_schema"	"OFF"
    "performance_schema_events_waits_history_long_size"	"10000"
    "performance_schema_events_waits_history_size"	"10"
    "performance_schema_max_cond_classes"	"80"
    "performance_schema_max_cond_instances"	"1000"
    "performance_schema_max_file_classes"	"50"
    "performance_schema_max_file_handles"	"32768"
    "performance_schema_max_file_instances"	"10000"
    "performance_schema_max_mutex_classes"	"200"
    "performance_schema_max_mutex_instances"	"1000000"
    "performance_schema_max_rwlock_classes"	"30"
    "performance_schema_max_rwlock_instances"	"1000000"
    "performance_schema_max_table_handles"	"100000"
    "performance_schema_max_table_instances"	"50000"
    "performance_schema_max_thread_classes"	"50"
    "performance_schema_max_thread_instances"	"1000"
    "pid_file"	"C:\winbin\mariadb-5.5.29-winx64\data\T470p.pid"
    "plugin_dir"	"C:\winbin\mariadb-5.5.29-winx64\lib\plugin\"
    "plugin_maturity"	"unknown"
    "port"	"3306"
    "preload_buffer_size"	"32768"
    "profiling"	"OFF"
    "profiling_history_size"	"15"
    "progress_report_time"	"56"
    "protocol_version"	"10"
    "query_alloc_block_size"	"8192"
    "query_cache_limit"	"1048576"
    "query_cache_min_res_unit"	"4096"
    "query_cache_size"	"0"
    "query_cache_strip_comments"	"OFF"
    "query_cache_type"	"ON"
    "query_cache_wlock_invalidate"	"OFF"
    "query_prealloc_size"	"8192"
    "range_alloc_block_size"	"4096"
    "read_buffer_size"	"131072"
    "read_only"	"OFF"
    "read_rnd_buffer_size"	"262144"
    "relay_log"	""
    "relay_log_index"	""
    "relay_log_info_file"	"relay-log.info"
    "relay_log_purge"	"ON"
    "relay_log_recovery"	"OFF"
    "relay_log_space_limit"	"0"
    "replicate_annotate_row_events"	"OFF"
    "replicate_do_db"	""
    "replicate_do_table"	""
    "replicate_events_marked_for_skip"	"replicate"
    "replicate_ignore_db"	""
    "replicate_ignore_table"	""
    "replicate_wild_do_table"	""
    "replicate_wild_ignore_table"	""
    "report_host"	""
    "report_password"	""
    "report_port"	"3306"
    "report_user"	""
    "rowid_merge_buff_size"	"8388608"
    "rpl_recovery_rank"	"0"
    "secure_auth"	"OFF"
    "secure_file_priv"	""
    "server_id"	"0"
    "shared_memory"	"OFF"
    "shared_memory_base_name"	"MYSQL"
    "skip_external_locking"	"ON"
    "skip_name_resolve"	"OFF"
    "skip_networking"	"OFF"
    "skip_show_database"	"OFF"
    "slave_compressed_protocol"	"OFF"
    "slave_exec_mode"	"STRICT"
    "slave_load_tmpdir"	"C:\Users\engels\AppData\Local\Temp"
    "slave_max_allowed_packet"	"1073741824"
    "slave_net_timeout"	"3600"
    "slave_skip_errors"	"OFF"
    "slave_sql_verify_checksum"	"ON"
    "slave_transaction_retries"	"10"
    "slave_type_conversions"	""
    "slow_launch_time"	"2"
    "slow_query_log"	"OFF"
    "slow_query_log_file"	"T470p-slow.log"
    "socket"	"MySQL"
    "sort_buffer_size"	"2097152"
    "sql_auto_is_null"	"OFF"
    "sql_big_selects"	"ON"
    "sql_big_tables"	"OFF"
    "sql_buffer_result"	"OFF"
    "sql_log_bin"	"ON"
    "sql_log_off"	"OFF"
    "sql_low_priority_updates"	"OFF"
    "sql_max_join_size"	"18446744073709551615"
    "sql_mode"	""
    "sql_notes"	"ON"
    "sql_quote_show_create"	"ON"
    "sql_safe_updates"	"OFF"
    "sql_select_limit"	"18446744073709551615"
    "sql_slave_skip_counter"	"0"
    "sql_warnings"	"OFF"
    "ssl_ca"	""
    "ssl_capath"	""
    "ssl_cert"	""
    "ssl_cipher"	""
    "ssl_key"	""
    "storage_engine"	"InnoDB"
    "stored_program_cache"	"256"
    "sync_binlog"	"0"
    "sync_frm"	"ON"
    "sync_master_info"	"0"
    "sync_relay_log"	"0"
    "sync_relay_log_info"	"0"
    "system_time_zone"	"Mitteleurop�ische Zeit"
    "table_definition_cache"	"400"
    "table_open_cache"	"400"
    "thread_cache_size"	"0"
    "thread_concurrency"	"10"
    "thread_handling"	"pool-of-threads"
    "thread_pool_max_threads"	"500"
    "thread_pool_min_threads"	"1"
    "thread_stack"	"294912"
    "time_format"	"%H:%i:%s"
    "time_zone"	"SYSTEM"
    "timed_mutexes"	"OFF"
    "tmp_table_size"	"16777216"
    "tmpdir"	"C:\Users\engels\AppData\Local\Temp"
    "transaction_alloc_block_size"	"8192"
    "transaction_prealloc_size"	"4096"
    "tx_isolation"	"REPEATABLE-READ"
    "unique_checks"	"ON"
    "updatable_views_with_limit"	"YES"
    "userstat"	"OFF"
    "version"	"5.5.29-MariaDB"
    "version_comment"	"mariadb.org binary distribution"
    "version_compile_machine"	"x86"
    "version_compile_os"	"Win64"
    "wait_timeout"	"28800"

--- 



